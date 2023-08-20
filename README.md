# PROJECT-2
## ***CREATING A LOAD BALANCER WITH THE HELP OF EC2 INSTANCE USING Nginx WEB SERVER***
### ROADMAP
With the help of EC2 Instance we will create a Load Balancer using the Nginx Web Server.
we will use three instances for checking the traffic if the Load Balancer is working correctly or not.
For data output we are using the ip of each instance in html page and different background colour of html page By which, we are able to find each instance with different colour.


### OVER-VIEW DIAGRAM

<img src="https://github.com/kitty6xt5/PROJECT2/blob/main/images/ec2loadbalancer.jpg">


### SOLUTION-------------------------------

### First of all we have to create an instance using ubuntu AMI.
<img src="">

### Launch the instance and connect it through ssh on terminal.
```
ssh -i "your key" ubuntu@(your publicip).compute-1.amazonaws.com
```
<img src="">

### After connecting the instance, type -
```
sudo apt update
```
<img src="">

### In cmd in terminal.
### Now we have to install some required services to move further in our process.
