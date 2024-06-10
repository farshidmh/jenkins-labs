# Installing a Plugin on Jenkins

## Lab Scenario

In this lab, you will learn how to install and configure a plugin on Jenkins. Jenkins plugins extend the functionality of Jenkins, providing features for various aspects of software development,
deployment, and integration. You will explore the Jenkins plugin ecosystem, install a plugin using the Jenkins plugin manager, and verify the installation and functionality of the plugin.

## Duration

30 minutes

## Objective

By the end of this lab, students will be able to:

- Understand the Jenkins plugin ecosystem.
- Install and configure a plugin from the Jenkins plugin manager.
- Verify the plugin installation and functionality.

## Prerequisites:

- Completion of the previous labs.
- Jenkins instance up and running.
- Admin access to the Jenkins dashboard.

## Step-by-step guide:

### Step A: Introduction to Jenkins Plugins

Jenkins plugins extend the functionality of Jenkins, providing features for various aspects of software development, deployment, and integration. The Jenkins plugin ecosystem is extensive, with
plugins available for build tools, version control systems, test reporting, and more.

### Step B: Accessing the Plugin Manager

1. **Login to Jenkins:**
    - Open a web browser and navigate to `http://<your-server-ip>:8080`.
    - Login with your admin credentials.

2. **Navigate to Plugin Manager:**
    - Go to **Manage Jenkins** from the left sidebar.
    - Click on **Plugins**.

### Step C: Exploring Available Plugins

1. **Available Tab:**
    - In the Plugin Manager, click on the **Available** tab.
    - You will see a list of available plugins that can be installed.

2. **Search for a Plugin:**
    - Use the search box to find a specific plugin. For this lab, we will install the "Blue Ocean".
    - Type "Blue Ocean" in the search box and press Enter.

### Step D: Installing the Plugin

1. **Select the Plugin:**
    - Find the **Blue Ocean** from the search results.
    - Check the box next to the plugin name.

2. **Install the Plugin:**
    - Click on the **Install** button at the top of the page.
    - **_DO NOT_** check the box that says "Restart Jenkins when installation is complete and no jobs are running".
    - Jenkins will download and install the plugin. You can monitor the installation progress.


3. **Wait for Installation to Complete:**
    - Once the installation is complete, a confirmation message will be displayed.
    - Once the installation is complete,go back to the home page, and you will see the Blue Ocean option in the left sidebar.

## Final File

There are no specific files to be submitted for this lab.

## Summary

In this lab, students learned how to install and configure a plugin on Jenkins. They explored the Jenkins plugin ecosystem, installed the Blue Ocean Plugin, and verified its installation and
functionality. This lab provided a foundational understanding of extending Jenkins capabilities through plugins.