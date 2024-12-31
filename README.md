# 3-Tier-AWS

#Introduction to a Three-Tier Architecture Project
A three-tier architecture is a software design pattern that organizes applications into three layers:
1)Presentation Layer (Web Tier): Handles user interactions. In this project, we'll use NGINX as the web server.
2)Application Layer (App Tier): Contains the backend logic. Here, we'll use Spring Boot for processing business logic.
3)Database Layer (Database Tier): Stores data persistently. We'll use Amazon RDS with MySQL as the database engine.

# Project Overview
The project is an employee management system where users can:
Add employee records through a web interface.
Retrieve, update, or delete employee data.

# Steps to implement:

# VPC and Subnets
Create a vpc and add subnets for vpc. I have created 8 subnets for app tier, db tier, web tier and public subnets for allowing incoming traffic from public loadbalancer.

![1subcal](https://github.com/user-attachments/assets/ce5e4d90-7a35-4f1f-8aab-89844233ceaf)

Here is the overview of subnets

![3createsubnets](https://github.com/user-attachments/assets/c7010f78-1221-43b2-b8d3-63e61c4178ef)


# Route Table
Create route tables (Public and Private). And associate the web, app and db subnets to private Routes. ANd for inbound and outbound traffic to public subnet associate a internet gateway to the vpc and public subnet. And create a NAT gateway in public subnet and add that to private subnet for internet acess to private instances.

![4RouteTable](https://github.com/user-attachments/assets/fb87ee80-0c01-4989-8647-517d49fa2c11)

![5IG](https://github.com/user-attachments/assets/3fb3b64f-2af0-4a37-bf66-1d8b4659965b)

![6NAT](https://github.com/user-attachments/assets/f8817cdb-c80c-4631-9f25-e600f13d358d)
