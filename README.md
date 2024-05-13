# Paweł Dzikiewicz - Terraform, EC2, TicTacToe report

- Course: *Cloud programming*
- Group: W04IST-SI0828G
- Date: 13.05.2024

## Environment architecture

BEANSTALK:

AWS Provider: Specifies the AWS region "us-east-1" and sets up the authentication using credentials stored at a local path.

VPC Configuration: Sets up a VPC named "my_vpc" with a CIDR block of "10.0.0.0/16", DNS support, and hostname resolution enabled.

Subnets:

Public Subnet: Created within the VPC with a CIDR of "10.0.101.0/24" in the "us-east-1a" zone, designed to allocate public IPs on instance launch.
Private Subnet: Also part of the VPC with a "10.0.102.0/24" CIDR in the "us-east-1b" zone.
Internet Gateway: An internet gateway named "my_igw" is attached to the VPC to facilitate outbound and inbound internet traffic.

Route Tables:

Public Route Table: Configured to route all outbound traffic to the internet via the internet gateway.
Security Group: Named "server_security", this security group is configured to allow inbound SSH, HTTP, and custom port 5000 traffic, with unrestricted outbound traffic.

Elastic Beanstalk Application:

Application: Defines an Elastic Beanstalk application named "my-docker-app" for managing Docker-based deployments.
Environment: Specifies an environment "my-docker-env2" under the application, set up with a specific solution stack for running ECS and various settings for VPC, subnets, instance profiles, public IP assignment, security groups, environment type, service roles, instance architectures, and instance types.
S3 Resources:

Bucket: An S3 bucket named "sianuga2-bucket" for storing application deployments.
Object: An object "CloudLab.zip" in the S3 bucket, specified for deployment in the Elastic Beanstalk environment.
Elastic Beanstalk Application Version: Sets up an application version "v1" using the specified S3 bucket and object key for deployment.

Output: Defines an output variable "app_url" that returns the URL to access the deployed application environment.

FARGATE:

Virtual Private Cloud (VPC)
Custom VPC: Named "my_vpc", has a CIDR block of "10.0.0.0/16", with DNS support and hostnames enabled.
Subnets
Public Subnet: Named "public_subnet", with a "10.0.101.0/24" CIDR block in "us-east-1a", enabling public IP mapping.
Private Subnet: Named "private_subnet", with a "10.0.102.0/24" CIDR block in "us-east-1b".
Internet Gateway
Gateway Configuration: An internet gateway, "my_igw", is attached to the VPC to facilitate communication with the internet.
Route Tables
Public Route Table: A route table ("public_route_table") with a route to the internet via the internet gateway is associated with both public and private subnets.
Security Groups
Server Security Group: Named "server_security", allows ingress on ports 22 (SSH), 80 (HTTP), and 5000 (HTTP for backend services) and unrestricted egress.
ECS Cluster
ECS Cluster: Named "app_cluster", hosts the ECS services and tasks.
ECS Task Definition
Task Definition: Named "app_task", configured to use the "FARGATE" launch type, specifies resource allocations and container definitions for the backend and frontend of the TicTacToe game.
ECS Service
Service Configuration: Named "app_service", runs the defined task in the specified cluster using FARGATE, with networking set to use the public and private subnets and the server security group.

## Preview

Screenshots of configured AWS services. Screenshots of your application running.

![Uploading image.png…]()


## Reflections

- What did you learn?
I learned how to setup beanstalk and fargate
- What obstacles did you overcome?
I worked through the problems like incorrect setup of Dockerrun and docker compose setup on remote
- What did you help most in overcoming obstacles?
  Documentation and stackoverflow
- Was that something that surprised you?
  Nothing has suprised me 
