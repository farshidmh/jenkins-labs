# Understanding and Creating a Jenkinsfile


## Duration
90 minutes

## Objective
By the end of this lab, students will be able to:
- Understand the purpose and structure of a Jenkinsfile.
- Create a Jenkinsfile for a simple Java project.
- Define various stages in a Jenkins pipeline using a Jenkinsfile.
- Utilize pipeline syntax and features to automate the build process.

## Prerequisites:
- Completion of the previous labs.
- Jenkins instance up and running.
- Basic knowledge of Jenkins and pipeline concepts.
- Java Development Kit (JDK) and Maven installed on the Jenkins server.
- Git installed on the Jenkins server.

## Step-by-step guide:

### Step A: Introduction to Jenkinsfile
1. **What is a Jenkinsfile?**
   - A Jenkinsfile is a text file that contains the definition of a Jenkins Pipeline and is checked into source control. It allows the entire build process to be automated and versioned alongside the code.

2. **Why use a Jenkinsfile?**
   - Enables the creation of complex build workflows using code.
   - Version control of the pipeline definition.
   - Improved visibility and auditing of the pipeline process.
   - Supports pipeline as code, making it easier to reproduce builds and share configurations.

### Step B: Setting Up the Java Project
1. **Create a New Directory for the Project:**
   - Open a terminal on your local machine.
   - Create a new directory for the Java project:
     ```bash
     mkdir JenkinsfileJavaProject
     cd JenkinsfileJavaProject
     ```

2. **Initialize a Git Repository:**
   - Initialize a new Git repository:
     ```bash
     git init
     ```

3. **Create a Simple Java Application:**
   - Create a directory structure for your Java project:
     ```bash
     mkdir -p src/main/java/com/example
     mkdir -p src/main/resources
     mkdir -p src/test/java/com/example
     ```
   - Create a simple Java class:
     ```java
     // src/main/java/com/example/App.java
     package com.example;

     public class App {
         public static void main(String[] args) {
             System.out.println("Hello, Jenkins Pipeline!");
         }
     }
     ```

4. **Create a `pom.xml` File:**
   - Create a `pom.xml` file in the root directory:
     ```xml
     <project xmlns="http://maven.apache.org/POM/4.0.0"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
         <modelVersion>4.0.0</modelVersion>
         <groupId>com.example</groupId>
         <artifactId>jenkinsfile-java-project</artifactId>
         <version>1.0-SNAPSHOT</version>
         <properties>
             <maven.compiler.source>1.8</maven.compiler.source>
             <maven.compiler.target>1.8</maven.compiler.target>
         </properties>
         <dependencies>
             <dependency>
                 <groupId>junit</groupId>
                 <artifactId>junit</artifactId>
                 <version>4.12</version>
                 <scope>test</scope>
             </dependency>
         </dependencies>
     </project>
     ```

5. **Commit the Project to Git:**
   - Add and commit the files to the Git repository:
     ```bash
     git add .
     git commit -m "Initial commit of Jenkinsfile Java project"
     ```

### Step C: Creating a Jenkinsfile
1. **Define the Pipeline:**
   - In your local Java project directory, create a file named `Jenkinsfile`:
     ```groovy
     pipeline {
         agent any
         tools {
             jdk 'Default'
             maven 'Default'
         }
         stages {
             stage('Checkout') {
                 steps {
                     git 'https://github.com/your-repo/JenkinsfileJavaProject.git'
                 }
             }
             stage('Build') {
                 steps {
                     sh 'mvn clean package'
                 }
             }
             stage('Test') {
                 steps {
                     sh 'mvn test'
                 }
             }
             stage('Archive') {
                 steps {
                     archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
                 }
             }
         }
         post {
             success {
                 echo 'Pipeline completed successfully!'
             }
             failure {
                 echo 'Pipeline failed.'
             }
         }
     }
     ```
   - Adjust the repository URL in the `git` step to point to your repository.

[WHAT IS THIS?](explain.md) 

2. **Commit the Jenkinsfile to Git:**
   - Add and commit the `Jenkinsfile` to your Git repository:
     ```bash
     git add Jenkinsfile
     git commit -m "Add Jenkinsfile for pipeline"
     git push origin main
     ```

### Step D: Setting Up Jenkins Pipeline Job
1. **Create a New Pipeline Job:**
   - Go to the Jenkins dashboard.
   - Click **New Item**, enter a name for the pipeline, select **Pipeline**, and click **OK**.

2. **Configure the Pipeline:**
   - In the **Pipeline** section, select **Pipeline script from SCM**.
   - Choose **Git** and enter the repository URL of your Java project.
   - For the **Script Path**, enter `Jenkinsfile`.

3. **Save the Job Configuration:**
   - Click **Save** to save the job configuration.

### Step E: Running the Pipeline
1. **Trigger the Pipeline:**
   - Go to the Jenkins dashboard and select your pipeline job.
   - Click **Build Now** to trigger the pipeline.

2. **Monitor the Build:**
   - Click on the build number to view the build details.
   - Monitor the console output to ensure that the stages are executed successfully.

3. **Verify the Artifacts:**
   - Once the build is complete, verify that the JAR file is generated and archived.
   - Go to the **Pipeline** job > **Build History** > **Artifacts** to download and verify the JAR file.

## Final File
Ensure the Jenkins pipeline is successfully set up and the JAR file is generated. Create a document listing:
- The URL of the Git repository containing the Java project and Jenkinsfile.
- A screenshot of the Jenkins pipeline execution showing the successful build and artifact archiving.

## Summary
In this lab, students learned about the purpose and structure of a Jenkinsfile. They created a Jenkinsfile for a simple Java project and defined various stages in a Jenkins pipeline. This lab provided hands-on experience with pipeline syntax and features, enabling students to automate the build process using Jenkinsfile.