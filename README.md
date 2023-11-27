# PROJECT-2
## ***CREATING A CUSTOM LOAD BALANCER WITH THE HELP OF EC2 INSTANCE USING Nginx WEB SERVER***
### ROADMAP
With the help of EC2 Instance we will create a Load Balancer using the Nginx Web Server.
we will use three instances for checking the traffic if the Load Balancer is working correctly or not.
For data output we are using the ip of each instance in html page and different background colour of html page By which, we are able to find each instance with different colour.



### OVER-VIEW DIAGRAM

![newww drawio](https://github.com/kitty6xt5/PROJECT2/assets/141032592/9881ac19-34f7-4fc3-bee4-f358892a6cd6)

### SOLUTION-------------------------------

### First of all we have to create an instance using ubuntu AMI.

![ami](https://github.com/kitty6xt5/PROJECT2/assets/141032592/4de10952-d934-4346-a233-3a1c855ca9aa)

### Launch the instance and connect it through ssh on terminal.
```
ssh -i "your key" ubuntu@(your publicip).compute-1.amazonaws.com
```
![ssh](https://github.com/kitty6xt5/PROJECT2/assets/141032592/9a5030b3-913b-4520-bf41-70d66763a794)

### After connecting the instance, type -
```
sudo apt update
```
It will download and installs the most recent packages, replacing any earlier versions that were already on your system. 

### Now we have to install some required services to move further in our process.
Now we have to install nginx webserver to create a Load balancer.to install nginx webserver type-

```
sudo apt install nginx -y

```
![nginxins](https://github.com/kitty6xt5/PROJECT2/assets/141032592/7a4e434a-3a84-4a7a-b6ff-5043e6c9f6be)

To check if the nginx server is working correctly copy paste the instance public ip and paste it on your browser.. if its working correctly you can see the default nginx page..

Now we have to delete or remove a file named as ```default``` to configure nginx..<v>
which is available at ```/etc/nginx/sites-enabled/```..to remove that file type-

```
rm -rf /etc/nginx/sites-enabled/default

```
![defdelete](https://github.com/kitty6xt5/PROJECT2/assets/141032592/697fea3d-3a72-4233-a81a-a11fa39ce842)

Now we have to create a file using ```.conf```...You can name it like anything you want. i am using here ```kitty.conf``` as my file name.

```
sudo vim /etc/nginx/conf.d/kitty.conf

```

![newconf](https://github.com/kitty6xt5/PROJECT2/assets/141032592/6c5b8563-830f-4595-b44c-b339c3b9db66)

Now we have to paste the script which is given below

```
upstream backend {
server 13.233.40.230; # type the public ip of those instance you created 
server 13.127.42.35; # type the public ip of those instance you created 
}
server {
Listen 80;
server_name 13.127.90.230;      # here type the public ip of your nginx instance 
 Location / {
proxy_redirect off;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $http_host;
proxy_pass http://backend;
}
}

```

Create 2 instances using ubuntu AMI.

![2ins](https://github.com/kitty6xt5/PROJECT2/assets/141032592/cd1e05f6-b311-4085-b20a-c6f7324bac7e)

Now scroll down and you will see an ```Advanced details``` option click on it and scroll down , you will see a ```userdata``` with box.<v> type these commands inside the box -

```
#!/bin/bash
apt update
apt install apache2 -y
systemctl start apache2


```
![user2](https://github.com/kitty6xt5/PROJECT2/assets/141032592/8b6fe2b0-bda7-40ab-8ef8-e484fd54b869)


Launch the instance.<v> 

SSH both instances and type- 

```
echo "<h1>heya its $(hostname)"<h1/> > /var/www/html/index.html

```

Now go back to the instance where you installed nginx and go to that file ```kitty.conf```.. <v>

First, we have to change the Nginx server ip address which is named as ```servername``` in the script with our public ip address. <v>

Now we have to copy paste the public ip of two instances which we are going to use and check it for our customised load balancer. <v>

Copy paste the public ip of two instances named after ```server``` in the script.. <v>

![111newconf-script](https://github.com/kitty6xt5/PROJECT2/assets/141032592/1bda5992-53df-4798-bd9c-58da01eb1bd5)

Restart ngnix

```
sudo systemctl restart ngnix

```

![restartnginx](https://github.com/kitty6xt5/PROJECT2/assets/141032592/4c71db01-0378-413c-8a4f-78f28a0c6bd2)

Now again copy the nginx instance public-ip and paste it on your browser, you can see whenever you refresh the page you will get the diffrent ip which means our custom load balancer is working Perfectly!!!!
