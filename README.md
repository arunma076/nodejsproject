## Setting up Jenkins, Ansible, and Docker Environment

## Introduction

This documentation outlines the process of setting up a Jenkins server, an Ansible server, and a Docker environment using Amazon EC2 instances. These servers will be used to create a pipeline for deploying a Node.js application to a Docker container using Ansible. Please follow these steps carefully to ensure a successful setup.

## Pre-Requisites
    • Amazon Web Services (AWS) account (for EC2 instances)
    • NPM
    • NodeJS
    
## Step 1: Create EC2 Instances

![image](https://github.com/arunma076/nodejsproject/assets/114279863/1e6a443e-b1cf-4179-ab88-7407b74c6b30)

Create three EC2 instances on AWS for Jenkins, Ansible, and Docker. Ensure that the security groups of these instances allow incoming connections from each other.

## Step 2: Jenkins Installation

2.1 Install Jenkins on the one the instance, follow the official documentation to install Jenkins.
https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

2.2 Install Required Jenkins Plugins

After Jenkins is installed, install the following plugins through the Jenkins web interface:
    • NodeJS Plugin
    • Publish Over SSH Plugin
    
2.3 Configure NodeJS Version
Configure the NodeJS version from the Jenkins configuration options.

## Step 3: Setup Ansible Server

3.1 Create an Ansible User
On the Ansible server, create a user for Ansible. Add this user to the sudoers file for passwordless access:

shellCopy code
echo "ans_user ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

3.2 Enable Password Authentication

Edit the SSH configuration file to enable password authentication in /etc/ssh/sshd_config.

shellCopy code
sudo vim /etc/ssh/sshd_config

3.3 Configure Jenkins SSH

In the Jenkins configuration, add the created Ansible user to the SSH configuration and test the connection to verify it works.

## Step 4: Jenkins Pipeline Setup

Now, you can create a Jenkins pipeline to copy Node.js application files to the Ansible server. When you run the pipeline, the files will be copied to the defined file location on the Ansible server.

## Step 5: Docker Installation on Ansible Server

Install Docker on the Ansible server and add the Ansible user to the Docker group. Additionally, create a Docker user and grant necessary permissions.

## Step 6: Build Docker Image

Write a Dockerfile and build the Docker image on the Ansible server. Test the Docker installation by installing Docker in the Ansible folder and verifying that it works as expected.

## Step 7: Install Ansible on Jenkins Server

On the Jenkins server, install Ansible using pip:

shellCopy code
sudo apt-get install python3-pip -y
pip install ansible

## Step 8: Ansible Playbook Setup

Create an Ansible playbook for running the Docker container in the target environment. Make sure to generate an SSH key pair using ssh-keygen -t rsa and configure it for passwordless SSH access.
Write the playbook for deploying the Docker container and test the results.

With these steps completed, you will have successfully set up a Jenkins pipeline for deploying a Node.js application to a Docker container using Ansible. Make sure to adapt these instructions to your specific environment and requirements.

![fdfgfgf](https://github.com/arunma076/nodejsproject/assets/114279863/f7b1025c-aaab-4d22-9f24-0c544edff284)

![Screenshot (177)](https://github.com/arunma076/nodejsproject/assets/114279863/a4edf974-2eb5-45f8-b531-3840e059de07)

![Screenshot (178)](https://github.com/arunma076/nodejsproject/assets/114279863/23093b69-17f9-4c0a-9fa5-67178e6ba276)

![image](https://github.com/arunma076/nodejsproject/assets/114279863/da04cee1-5722-4eb7-b479-817d98d4959e)








