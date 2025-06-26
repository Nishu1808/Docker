# Docker
Docker Example :

- Get plain Alpine image

- Install Nodejs (RUN)

- Install npm (RUN)

- Create new dir (RUN)

- set that dir as working dir

- create new angular project (RUN)

- Expose PORT 4200

- CMD -> ng serve
 
----------------------------------

Connect to EC2 =>

Install docker and Create Dockerfile

contents =>
 
FROM alpine

RUN apk add --update nodejs npm; \

    npm install -g @angular/cli; \

    mkdir mytest

WORKDIR /mytest

RUN ng new my-first-project

EXPOSE 4200

CMD cd my-first-project && ng serve --host 0.0.0.0 --disable-host-check
 
-----------------------------------
 
Build docker image :

sudo docker build -t mynewalpine .
 
Run docker image in detached mode :

sudo docker run -d -p 4200:4200 myalpine
 
Access Angular Application :
http://ec2-3-xx-xx-5.ap-south-1.compute.amazonaws.com:4200/
 
To get Docker running on the AWS AMI you should follow the steps below (these are all assuming you have ssh'd on to the EC2 instance).
 
Update the packages on your instance
 
[ec2-user ~]$ sudo yum update -y
 
Install Docker
 
[ec2-user ~]$ sudo yum install docker -y
 
Start the Docker Service
 
[ec2-user ~]$ sudo service docker start
 
Add the ec2-user to the docker group so you can execute Docker commands without using sudo.
 
[ec2-user ~]$ sudo usermod -a -G docker ec2-user
 
Exit and relogin
 
