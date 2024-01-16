# Deploying A Simple node-js website

This is a simple node-js website[code is freely available on internet ] which I am going to use to deploy it on a Virtual Machine.Here I am using AWS[cloud service provider] EC2 instance.

* Create an AWS account
* Go to EC2 instance -> Lauch Instance 
* Choose **Ubuntu** image [here using 22.04 LTS (free tier eligible)] and instance type **t2.micro** [it is in free tier] generate a key pair(RSA -> .pem type)[it will download a pem file to your local ,keep it safe it will be used to connect your instance through ssh]

* Keep others as default and click **Launch Instance**

## Connect Your Instance Through ssh
  * If you are using Linux just open terminal 
  * The latest builds of Windows 10 and Windows 11 include a built-in SSH server and client that are based on OpenSSH
  * Or you can use any other software like **PuTTY**
  To connect to the instance 1st go to the directory or copy the path where your pem file is saved and run

```bash
  ssh -i /path/key-pair-name.pem <instance-user-name>@<instance-public-IP>
```
Type **yes** 

#### Update server packages on Ubuntu
```bash
 sudo apt update
```
#### Install **Node.js**  and **npm** pacakges 
```bash
 sudo apt install Node.js
 sudo apt install npm
```
#### Check the packages are properly installed or not [check the version]
```bash
 Node.js -v && npm --version
```
#### Clone my git Repository
```bash
 git clone https://github.com/MohanPiru/Deploy-Website-on-VM.git 
```
#### Go to the 'nodejs-website' folder 
```bash
 cd Deploy-Website-on-VM/nodejs-website/
```
#### Run this command [This command will install the dependencies defined in "package.json" file] 

```bash
 npm install
```
#### Now run this 
```bash
 npm start
```
#### The website is now running on port "3000"  [mentioned in server.js file]

* To see it you need to add a rule in your security group of VM instance.
* Go to security settings of your instance -> security group -> add rule[outbound] -> add port 3000 [tcp]

Now serach it in your browser
```bash
 <your vm public ip>:3000
```
## You can see your website running ...

**distroless-image Dockerfile will create a image of 89mb only but the actual Dockerfile will create 1.1gb image**
