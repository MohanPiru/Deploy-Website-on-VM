
# Deploying A Simple JavaScript Website

This is a simple javascript website[code is freely available on internet ] which I am going to use to deploy in on a Virtual Machine.Here I am using AWS[cloud service provider] EC2 instance.

* Create an AWS account
* Go to EC2 instance -> Lauch Instance 
* Choose **Ubuntu** image [here using 22.04 LTS (free tier eligible)] and instance type **t2.micro** [it is in free tier] generate a key pair(RSA -> .pem type)[it will download a pem file to your local ,keep it safe it will be used to connect your instance through ssh]
* You will choose the type of traffic your “virtual Machine” will allow from the outside. You need to allow two types of traffic  **SSH** (so we can “log in” to the virtual Machine) and **HTTP** (so we can view our webpage through the browser).
* Keep others as default and click **Launch Instance**

### Connect Your Instance Through ssh
  * If you are using Linux just open terminal 
  * The latest builds of Windows 10 and Windows 11 include a built-in SSH server and client that are based on OpenSSH
  * Or you can use any other software like **PuTTY**



To connect to the instance 1st go to the directory or copy the path where your pem file is saved and run

```bash
  ssh -i /path/key-pair-name.pem <instance-user-name>@<instance-public-IP>
```
Type **yes** 
### Update server packages on Ubuntu
```bash
 sudo apt update
```
### Install Apache 
 Apache is the web server that processes requests and serves web assets and content via HTTP.
 ```bash
 sudo apt install apache2 -y
```
### Clone my git Repository
```bash
 git clone https://github.com/MohanPiru/Deploy-Website-on-VM.git 
```
### Move all files to /var/www/html
```bash
sudo mv Deploy-Website-on-VM/Simple-Javascript-website/demo-website/* /var/www/html/

```
**/var/www/html** is just the default root folder of the web server or the folder you want to install your website on.
### Start Apache service
```bash
 sudo systemctl start apache2
```
### Now You can see your website running  

Copy the  public ip of your instance and paste it in your browser 


## If you choose Amazon linux as an image of your instance run these commands
```bash
 yum update -y
```
```bash
yum install httpd -y
```
```bash
 cd /var/www/html
```
```bash
git clone https://github.com/MohanPiru/Deploy-Website-on-VM.git 
```
```bash
 mv Deploy-Website-on-VM/Simple-Javascript-website/demo-website/* .
```
```bash
service httpd start
```
## How to delete Apache server from your System
Run the following commands 
```bash
sudo service apache2 stop
```
```bash
sudo apt-get purge apache2 apache2-utils apache2.2-bin apache2-common
```
```bash
sudo apt-get autoremove
```
```bash
whereis apache2
```
After this command if you get "apache2: /etc/apache2" this type of output , copy the all output locations[it can be more than one] where there is apache2 and run the following 
```bash
sudo rm -rf <"/etc/apache2" - replace it by all the locations>
```
