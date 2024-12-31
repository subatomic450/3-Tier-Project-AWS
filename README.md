# 3-Tier-Project-AWS

#Introduction to a Three-Tier Architecture Project
A three-tier architecture is a software design pattern that organizes applications into three layers:

1)Presentation Layer (Web Tier): Handles user interactions. In this project, we'll use NGINX as the web server.

2)Application Layer (App Tier): Contains the backend logic. Here, we'll use Node jS for processing business logic.

3)Database Layer (Database Tier): Stores data persistently. We'll use Amazon RDS with MySQL as the database engine.

# Project Overview
The project is an employee management system where users can:

Add employee name and email through a web interface.

Retrieve, update, or delete data.


https://github.com/user-attachments/assets/a15a7b30-0ab3-4d93-ae85-7bae52a91457


# Steps to implement:

# VPC and Subnets
Create a vpc and add subnets for vpc. I have created 8 subnets for app tier, db tier, web tier and public subnets for allowing incoming traffic from public loadbalancer.

![1subcal](https://github.com/user-attachments/assets/ce5e4d90-7a35-4f1f-8aab-89844233ceaf)

Here is the overview of subnets

![3createsubnets](https://github.com/user-attachments/assets/c7010f78-1221-43b2-b8d3-63e61c4178ef)


# Route Tables and Gateways
Create route tables (Public and Private). And associate the web, app and db subnets to private Routes. And for inbound and outbound traffic to public subnet associate a internet gateway to the vpc and public subnet. Also create a NAT gateway in public subnet and add that to private subnet for internet acess to private instances.

![4RouteTable](https://github.com/user-attachments/assets/fb87ee80-0c01-4989-8647-517d49fa2c11)

![5IG](https://github.com/user-attachments/assets/3fb3b64f-2af0-4a37-bf66-1d8b4659965b)

![6NAT](https://github.com/user-attachments/assets/f8817cdb-c80c-4631-9f25-e600f13d358d)


# SSM Role
Create a ssm role and later attach to all the instances to connect
![7Role](https://github.com/user-attachments/assets/321d9ed5-21fc-4cf2-9b9f-ed314be73f0e)

# EC2 Instances

Create App tier and Web tier instances. I have created Linux machines that are running on Ubuntu.

![8Instances](https://github.com/user-attachments/assets/94248ba0-c6b3-48ca-aa56-3416571c0787)

# Create Database Engine
First create a DataBase subnet group and add db subnets to that group. Later create a database. I have used MySql.
![9RDSSubnetGroup](https://github.com/user-attachments/assets/630f2439-2753-4e62-a9de-0ab1d5ce3d04)
![10RDSEngine](https://github.com/user-attachments/assets/9c9360a7-61a0-4c4c-a3cd-412cadcc1d09)


# External and Internal LoadBalancers
Create a external loadbalancer and associate web servers in target group. For the Internal Loadbalancers associate App servers.

![14LB](https://github.com/user-attachments/assets/39906f18-6496-4a67-b5c6-32f8c3d65e54)

![18-ILB-3000-Listener](https://github.com/user-attachments/assets/37092f41-e54b-4d31-8a4f-77ad80efca34)

# Configurations
## Web Servers
Connect to Web servers and install nginx and copy the html pages to /var/www/html/. (Edit the Ip address of Internal LoadBalancer in the code)
## App Servers
Connect to App servers and install Node.JS and MySql. 

### Prepare Database:
Create an RDS MySQL instance.

Run the following SQL commands to create the database and table:

CREATE DATABASE user_management;
USE user_management;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL
);

Edit the Config file

### Install Node.js


sudo apt update
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs

Install dependencies and start the server on app folder:

cd /home/ec2-user/app
npm install
node app.js (To start the service)

![100](https://github.com/user-attachments/assets/21bd48aa-7a79-41e2-9c73-6056648a6114)

![101Connect](https://github.com/user-attachments/assets/f347c6ae-9b32-4e10-beee-435423739f3d)


# Output

https://github.com/user-attachments/assets/4f1984dd-122e-4709-9946-79b64ea86cef

