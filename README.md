# PROJECT-2
## ***CREATING A CUSTOM LOAD BALANCER WITH THE HELP OF EC2 INSTANCE USING Nginx WEB SERVER***
### ROADMAP
With the help of EC2 Instance we will create a Load Balancer using the Nginx Web Server.
we will use three instances for checking the traffic if the Load Balancer is working correctly or not.
For data output we are using the ip of each instance in html page and different background colour of html page By which, we are able to find each instance with different colour.



![defdelete](https://github.com/kitty6xt5/PROJECT2/assets/141032592/697fea3d-3a72-4233-a81a-a11fa39ce842)
![ec2load-balancer](https://github.com/kitty6xt5/PROJECT2/assets/141032592/b9ad2903-446b-4801-915e-f7a7a4996877)
![newconf](https://github.com/kitty6xt5/PROJECT2/assets/141032592/6c5b8563-830f-4595-b44c-b339c3b9db66)
![newconf-script](https://github.com/kitty6xt5/PROJECT2/assets/141032592/1c467603-a8bd-4cfe-9d5c-2a61930d0df2)


![restartnginx](https://github.com/kitty6xt5/PROJECT2/assets/141032592/4c71db01-0378-413c-8a4f-78f28a0c6bd2)

### OVER-VIEW DIAGRAM

![custom](https://github.com/kitty6xt5/PROJECT2/assets/141032592/7b13ac71-5d7c-42d0-869c-27d2f738408b)

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
### In cmd in terminal.
### Now we have to install some required services to move further in our process.
Now we have to install nginx webserver to create a Load balancer.to install nginx webserver type-

```
sudo apt install nginx -y

```
![nginxins](https://github.com/kitty6xt5/PROJECT2/assets/141032592/7a4e434a-3a84-4a7a-b6ff-5043e6c9f6be)

To check if the nginx server is working correctly copy paste the instance public ip and paste it on your browser.. if its working correctly you can see the deafault nginx page..
