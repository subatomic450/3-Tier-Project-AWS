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

![3createsubnets](https://github.com/user-attachments/assets/c7010f78-1221-43b2-b8d3-63e61c4178ef)
