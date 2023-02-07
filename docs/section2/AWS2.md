  # Section 2: Part 2: [AWS] Wordpress on ECS 

## Objectives

Project 6 required me to:
- Set up Wordpress in EC2 
- Have an RDS database connected to wordpress
- Push the Wordpress container to ECR

## Getting Started
Project 5 took 1 day, but Project 6 took 2 weeks.

### EC2
Developed tbe wordpress container until it was working on a single EC2 instance.
  - Install docker and git on an EC2 instance
  - yum install docker
  - yum install git  
  - Clone my wordpress repo from Github
  - git clone my [Wordpress on AWS repo](https://github.com/gitsugatensho/WPonAWS.git) 
  - edit credentials in docker-compose.yml file.
  - run docker-compose up -d
  - Edit the docker-compose.yml file until it was fully working

### RDS
- Set up an RDS database and linked it to the single EC2 instance to check if it was working.
### ELB options
Elb was in a previous version of project 6 but was ommitted in a new version as it was not in the requirements for project 6. 
### EFS issue
EFS integration was not successful in the earlier version and since it was not in the requirements either, it was omitted. 
### Port and Environmental Variable issues
Port values and Environmental values were not set correctly on multiple occasions, so extra care was taken to ensure that the right values were being enterred in data fields across the AWS interface.
### Pushing the container to ECR
- Set AWS credentials
- Login to AWS
  ```console
  aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin ************.dkr.ecr.eu-west-2.amazonaws.com
  ```
- Push image to ECR repository
  ```bat
  - docker tag wordpressimage:latest ************.dkr.ecr.eu-west-2.amazonaws.com/wordpressblog:latest
  ```
  ```console
  - docker push ************.dkr.ecr.eu-west-2.amazonaws.com/wordpressblog:latest
  ```
### next
- Created a task definition that used the image from ECR repository wordpressblog 
- The ports were mapped to port 80.
Environmental variables were set:
Wordpress_config_extra is for any extra constants
DB host points to the RDS database
And the rest are the credentials for the wordpress database.

### Points of failure:
EFS mounting issue
Container port not specified
Wrong container port 
No environmental variables specified
Wrong environmental variables
RDS password different to what it was supposed to be
Security groups with missing rules
 
 ## Relevant links

[Home](/index) | [About](/about) | [License](/license) | [Docs](/section1)
