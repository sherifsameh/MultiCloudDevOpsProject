# MultiCloudDevOpsProject
# Project Overview: Automated DevOps Pipeline for a Spring Boot Application

## Introduction

This project aims to establish a fully automated DevOps pipeline for deploying a Spring Boot application. Leveraging a suite of powerful tools including Jenkins, OpenShift, Terraform, Ansible, and Docker, the project embodies the principles of Infrastructure as Code (IaC), Continuous Integration (CI), and Continuous Deployment (CD). The end goal is to achieve streamlined, automated, and efficient deployment processes with robust monitoring and alerting capabilities.

<p align="center"><img src="screenshots/Architecture.png" width="90%" height="90%">
<br><em>Architecture</em>
</p>


## Requirements
- :white_circle: GitHub
- :white_circle: AWS 
- :white_circle: Terraform
- :white_circle: Ansible
- :white_circle: Docker
- :white_circle: SonarQube
- :white_circle: Openshift cluster


## Project Components

### 1. Spring Boot Application Deployment Using Jenkins on OpenShift

The objective of automating the deployment of a Spring Boot application within an OpenShift cluster is achieved through Jenkins. By developing Jenkins pipelines that efficiently manage the deployment lifecycle from code commit to production deployment, we ensure a scalable and resilient process. 


### 2. AWS Infrastructure Provisioning Using Terraform

Provision and manage a complete AWS infrastructure using Terraform, enabling IaC practices. This approach not only streamlines the creation of AWS resources but also integrates them with CloudWatch for monitoring and alerting.

**Deploying the terraform modules to provision resources:**
* Install AWS CLI and add your AWS user access key and secret access key to enable

```shell
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
$ aws configure
```
<p align="center"><img src="screenshots/terraform/terraform tree last.png" width="90%" height="90%">
<br><em>Terraform structure</em> 
</p>

<p align="center"><img src="screenshots/terraform/final terraform.png" width="90%" height="90%">
<br><em>Terraform apply results</em> 
</p>

### 3. EC2 Instance Configuration Using Ansible
Utilizing Ansible for configuring AWS EC2 instances to host services such as Git, Docker, Java, Jenkins, SonarQube, and OpenShift. This approach ensures consistent and repeatable setups across instances, leading to fully configured and operational EC2 instances ready to support various stages of the DevOps pipeline.
1. Create a key pair on AWS. Download it to be used in the dynamic inventory and change its permissions as follows:
```shell
$ chmod 400 IvolveKey.pem
```
2. Run the ansible playbook using the following command
```shell
$ ansible-playbook -i inventory/aws_ec2.yml playbook.yml
```
<p align="center"><img src="screenshots/Ansible/ansible structure.png" width="90%" height="90%">
<br><em>Ansible structure</em> 
</p>

<p align="center"><img src="screenshots/Ansible/asnible playbook amazon linux run.png" width="90%" height="90%">
<br><em>Ansible-playbook results on Ec2</em> 
</p>

<p align="center"><img src="screenshots/Ansible/ansible playbook in the local inventory.png" width="90%" height="90%">
<br><em>Ansible-playbook results on local machines</em> 
</p>

<p align="center"><img src="screenshots/Ansible/connect to ec2.png" width="90%" height="90%">
<br><em>Connect to your Ec2</em> 
</p>

<p align="center"><img src="screenshots/Ansible/sonarqube login.png" width="90%" height="90%">
<br><em>SonarQube login</em> 
</p>

<p align="center"><img src="screenshots/Ansible/create local project sonar.png" width="90%" height="90%">
<br><em>Create SonarQube project</em> 
</p>

### 4. Centralized Monitoring and Logging with OpenShift
Implement a centralized monitoring and logging system within the OpenShift cluster. We gain insights into application performance and overall cluster health, thus enhancing operational visibility and intelligence.

### 5. Containerization of the Java Application

Containerizing the Java application is a key part of this project, ensuring environment consistency and ease of deployment. The development of a Dockerfile, detailing all dependencies and configurations, leads to a containerized version of the Java application. 

<p align="center"><img src="screenshots/docker/docker build .png" width="90%" height="90%">
<br><em>Docker build results</em> 
</p>

<p align="center"><img src="screenshots/docker/docker image run localhost 8081.png" width="90%" height="90%">
<br><em>Accessing Application </em> 
</p>

### 6. CI/CD Automation with Jenkins

Automate the CI/CD process using Jenkins, thereby streamlining the application deployment lifecycle. The development of a Jenkins pipeline script integrates various stages, including code build, testing, and deployment. This results in a seamless, automated pipeline that accelerates the release cycle and reduces manual intervention.

<p align="center"><img src="screenshots/jenkins/jenkins final pipeline run.png" width="90%" height="90%">
<br><em>Success Pipeline</em> 
</p>

<p align="center"><img src="screenshots/jenkins/test.png" width="90%" height="90%">
<br><em>Unit Test</em> 
</p>

<p align="center"><img src="screenshots/jenkins/pushed to dockerhub.png" width="90%" height="90%">
<br><em>Jenkins compile Pushing to docker hub</em> 
</p>

<p align="center"><img src="screenshots/jenkins/push to docker hub final.png" width="90%" height="90%">
<br><em>Build and Push to docker hub</em> 
</p>

<p align="center"><img src="screenshots/jenkins/deploy to openshift.png" width="90%" height="90%">
<br><em>Deploy to openshift and create the resources </em> 
</p>

<p align="center"><img src="screenshots/jenkins/Deployments.png" width="90%" height="90%">
<br><em>Deployment in the openshift cluster</em> 
</p>

<p align="center"><img src="screenshots/jenkins/Service.png" width="90%" height="90%">
<br><em>Service created </em> 
</p>

<p align="center"><img src="screenshots/jenkins/Route.png" width="90%" height="90%">
<br><em>Route created </em> 
</p>

<p align="center"><img src="screenshots/jenkins/access application.png" width="90%" height="90%">
<br><em>Accessing the Application using route</em> 
</p>

## Conclusion

This project successfully combines various advanced tools to create an efficient and automated system for deploying and managing a Spring Boot application. By using Jenkins for automation, OpenShift for orchestration, Terraform for setting up AWS infrastructure, Ansible for configuration, and Docker for containerization, we've streamlined the entire deployment process. This approach not only makes deploying applications quicker and more reliable but also ensures consistent performance and easy monitoring. The result is a straightforward, effective, and modern solution that meets the demands of today’s fast-paced software development and deployment needs.
