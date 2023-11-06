# aws-three-tier-webapp-architecture
Deploy a three tier web application on AWS - end to end demo

Use Case: To build a highly available, scalable three tier web-app using AWS cloud services

### Description

In this end to end demo, we will be build and deploy a highly avaible and scalable three tier web architecture manually using AWS console. Assumption is that you have at least some foundational knowledge around VPC, EC2, RDS, S3, ELB.


### Architecture 

![image](https://github.com/amazinglyaws/aws-three-tier-webapp-architecture/assets/133778900/b7a167a9-cdee-4d09-b6c9-e7ce8d1176e1)

### Pre-requisites
- Setup an AWS free tier (if there is none)
  
#### 01- Initial Setup
- Download code from GitHubgit
```
  clone https://github.com/aws-samples/aws-three-tier-web-architecture-workshop.git
```
- Create S3 bucket
- Create IAM EC2 Instance Role

#### 02- Networking and Security
- Create VPC and Subnets
- Create Internet Gateway (IGW)
- Setup Routing
- Create Security Groups (SG)

#### 03- Deploy Database
- Create Subnet Groups
- Deploy Databae

#### 04- Deploy App Tier Instance
- Deploy the App from S3
- Connect to App Instance
- Configure Database
- Configure App Instance
- Test App Tier

#### 05- Setup Internal Load Balancing and Auto Scaling (for App Tier)
- Create App Tier AMI (for auto-scaling)
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
