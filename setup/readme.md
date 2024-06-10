# Installing Jenkins on Ubuntu Using Docker

## Lab Overview

Jenkins is an open-source automation server that helps automate the building, testing, and deployment of software applications. In this lab, students will learn how to install Jenkins on an Ubuntu
system using Docker. Docker is a platform that allows developers to automate the deployment of applications inside lightweight, portable containers. By the end of this lab, students will have a
running Jenkins server accessible through a web browser.

## Duration

60 minutes

## Objective

By the end of this lab, students will be able to:

- Understand the basics of Docker.
- Install Docker on an Ubuntu system.
- Pull and run the Jenkins Docker container.
- Access the Jenkins UI through a web browser.

## Prerequisites:

- Basic knowledge of command-line operations.
- An Ubuntu machine with internet access.
- User with sudo privileges on the Ubuntu machine.

## Step-by-step guide:

### Step A: Introduction to Docker

Docker is a platform that allows developers to automate the deployment of applications inside lightweight, portable containers. Containers include everything needed to run an application, including
the code, runtime, libraries, and system tools.

### Step B: Update the System

1. Open a terminal.
2. Update your package list to ensure you have the latest version of the repositories:
   ```bash
   sudo apt-get update
   ```

### Step C: Install Docker

1. Install the necessary packages for Docker installation:
   ```bash
   sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
   ```
2. Add Docker’s official GPG key:
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```
3. Add Docker’s APT repository:
   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```
4. Update your package list again to include Docker’s repository:
   ```bash
   sudo apt-get update
   ```
5. Install Docker CE (Community Edition):
   ```bash
   sudo apt-get install docker-ce
   ```
6. Verify Docker installation:
   ```bash
   sudo systemctl status docker
   ```

### Step D: Pull and Run the Jenkins Docker Container

1. Pull the official Jenkins image from Docker Hub:
   ```bash
   sudo docker pull jenkins/jenkins:lts-jdk17
   ```
2. Run the Jenkins container:
   ```bash
   sudo docker run -d -p 8080:8080 -p 50000:50000 --name jenkins jenkins/jenkins:lts-jdk17
   ```
    - `-d`: Run the container in detached mode (in the background).
    - `-p 8080:8080`: Map port 8080 of the host to port 8080 of the container (for Jenkins UI).
    - `-p 50000:50000`: Map port 50000 of the host to port 50000 of the container (for Jenkins agent connections).
    - `--name jenkins`: Assign the name “jenkins” to the container.

### Step E: Access Jenkins UI

1. Open a web browser.
2. Navigate to `http://<your-server-ip>:8080`.
3. You will see the Jenkins setup wizard page. Follow the instructions to complete the setup.

### Step F: Unlock Jenkins

1. Retrieve the initial admin password from the Jenkins container:
   ```bash
   sudo docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
   ```
2. Copy the password and paste it into the Jenkins setup wizard to unlock Jenkins.

### Step G: Customize Jenkins and Install Plugins

1. Choose "Install suggested plugins" for a basic setup.
2. Wait for the plugins to install.
3. Create your first admin user and complete the setup.

## Final File

There are no specific files to be submitted for this lab. Ensure that Jenkins is running and accessible via the web browser.

## Summary

In this lab, students learned how to install Docker on an Ubuntu system, pull the Jenkins Docker image, and run the Jenkins container. They accessed the Jenkins UI through a web browser and completed
the initial setup, making Jenkins ready for use. This foundational knowledge will enable students to use Jenkins for continuous integration and continuous deployment tasks.