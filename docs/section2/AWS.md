# Section 2: Part 1: (AWS EC2)

## Previously
- Created AWS account
- Setup 2FA
- Setup IAM roles
- Followed an introductory course and was briefly informed about all of the AWS technologies.
## Project 4
##### Hosting a Docker app on an EC2 instance on AWS. 
- The first step was to create an EC2 instance and connect to it via SSH. 
    - Used Amazon Linux 2 as the image and used the free tier AMI t2.nano.
    - I generated a key pair called "project4key" and downloaded the relevant .pem onto my local device.
    - Created a security group and set inbound and outbound traffic rules. 
        - ![Inbound Rules](/images/InboundRulesP4.png)
        *Inbound rules - port 80 is where the docker image will be hosted, port 443 to allow traffic via HTTPs, and port 22 allows for me to connect to the linux image via SSH*
        - ![Outbound Rules](/images/OutboundRulesP4.png)
        *Outbound rules - there is no restriction on which ports and IPs traffic can leave out to*
    - I used the command <code>ssh -i "project4key.pem" ec2-user@ec2-13-40-235-185.eu-west-2.compute.amazonaws.com</code> to connect to the linux image via SSH. 
- The next step was to install dependencies.
    - I used sudo su to access root user privileges and installed git and docker.
    - I pulled my repo [gifsite]("github.com/gitsugatensho/gifsite). This repo contains a Dockerfile, and a flask app that displays a random gif upon visiting the site. 
    ![Gifsite](/images/GifSite.png)
    *The gif site! (ignore that it says 'cat fif' and shows a gif of Timmy the sheep*
    - I built the docker image within my repo and ran it. The docker app was being hosted on port 80.


##### Launch Templates and Auto Scaling Groups
- Create a launch template 
    - Having trouble with this
    - Didn’t do it correctly.
- Create auto scaling group 
    - What’s a use case for this in a work project?
    - How can I schedule stop/start with time of the day?
- Understand horizontal and vertical scaling 
    - Understood.



## Relevant links

[Home](/index) | [About](/about) | [License](/license) | [Docs](/section1)
