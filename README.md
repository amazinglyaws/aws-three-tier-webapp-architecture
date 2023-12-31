# Building an AWS three tier webapp architecture
Deploy a three tier web application on AWS - end to end

Use Case: To build a highly available, scalable three tier web-app using AWS cloud services

### Description

In this end to end demo, we will be build and deploy a highly available and scalable three tier web  application architecture using AWS console. Assumption is that you have at least some foundational knowledge around VPC, EC2, RDS, S3, ELB etc.


### Architecture 

In our architecture, client traffic is forwarded to our web tier EC2 instances using a public-facing Application Load Balancer. The web tier is running Nginx webservers that are configured to serve a React.js website. This web tier redirects our API calls to the application tier’s internal facing load balancer. The internal facing load balancer then forwards that traffic to the application tier, which is written in Node.js. The application tier manipulates data in an Aurora MySQL multi-AZ database and returns it to our web tier. Load balancing, health checks and autoscaling groups are created at each layer to maintain the availability of this architecture.

![image](https://github.com/amazinglyaws/aws-three-tier-webapp-architecture/assets/133778900/a64db79a-be5e-44c7-aa7b-6c9caab1249a)


### Pre-requisites
- An AWS account (free tier should work)
- An IDE/Text Editor of your choice (VS Code recommended)
  
#### 01- Initial Setup
- Download code from GitHub
  ```
    git clone https://github.com/amazinglyaws/aws-three-tier-webapp-architecture.git
  ```
- Create S3 bucket
- Create IAM EC2 Instance Role

#### 02- Networking and Security
- Create VPC and Subnets
- Create Internet Gateway and NAT Gateways (for public subnets)
- Setup Routing
- Create Security Groups (SG)

#### 03- Deploy Database
- Create Subnet Groups
- Deploy RDS Aurora Database
  takes about 20 minutes to start the database

#### 04- Deploy App Tier Instance
- Deploy the App from S3
- Connect to App Instance
- Configure Database

```
  sh-5.2$ sudo yum install mysql
  Last metadata expiration check: 1:01:40 ago on Mon Nov  6 18:27:05 2023.
  No match for argument: mysql
  Error: Unable to find a match: mysql
```

If you get the above error, follow the below steps

The Amazon Linux 2023 repository does not seem to contain MySQL.
https://docs.aws.amazon.com/linux/al2023/release-notes/support-info-by-package.html

Therefore, the following installation procedure must be used.

```
  sudo su -
  dnf -y localinstall https://dev.mysql.com/get/mysql80-community-release-el9-4.noarch.rpm
  dnf -y install mysql mysql-community-client
```

- Configure App Instance
- Test App Tier

#### 05- Setup Internal Load Balancing and Auto Scaling (for App Tier)
- Create App Tier AMI (for auto-scaling)
  - NodeJS application runs of port 4000
- Create Target Group
- Create Internal Load Balaner (NLB)
- Create Launch Template
- Create Auto Scaling Group

#### 06- Deploy Web Tier Instance
- Update nginx conf
- Deploy Web Instance
- Connect to Instance
- Configure Web Instance

#### 07 - Setup External Load Balancing and Auto Scaling (for Web Tier)
- Create Web Tier AMI (for auto-scaling)
- Create Target Group
- Create Internet Facing Load Balancer (ALB)
- Create Launch Template
- Create Auto Scaling Group

#### 08 - Conclusion
- Test the application
- Clean up AWS resources
