# Creating a Freestyle Job with Java in Jenkins


## Duration
60 minutes

## Objective
By the end of this lab, students will be able to:
- Create a Freestyle job in Jenkins.
- Configure the job to build a Java project using Maven.
- Execute the job and verify the build results.

## Prerequisites:
- Completion of the previous labs.
- Jenkins instance up and running.
- Basic knowledge of Java and Jenkins.
- Java Development Kit (JDK) and Maven installed on the Jenkins server.
- Git installed on the Jenkins server.

## Step-by-step guide:

### Step A: Setting Up the Java Project
1. **Create a New Directory for the Project:**
   - Open a terminal on your local machine.
   - Create a new directory for the Java project:
     ```bash
     mkdir FreestyleJavaProject
     cd FreestyleJavaProject
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
             System.out.println("Hello, Jenkins Freestyle Job!");
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
         <artifactId>freestyle-java-project</artifactId>
         <version>1.0-SNAPSHOT</version>
         <properties>
             <maven.compiler.source>1.8</maven.compiler.source>
             <maven.compiler.target>1.8</maven.compiler.target>
         </properties>
         <dependencies>
             <dependency>
                <groupId>junit</groupId>
				<artifactId>junit</artifactId>
				<version>3.8.1</version>
				<scope>test</scope>
             </dependency>
         </dependencies>
     </project>
     ```

5. **Commit the Project to Git:**
   - Add and commit the files to the Git repository:
     ```bash
     git add .
     git commit -m "Initial commit of Freestyle Java project"
     ```

### Step B: Setting Up Jenkins Freestyle Job
1. **Create a New Freestyle Job:**
   - Go to the Jenkins dashboard.
   - Click **New Item**, enter a name for the job, select **Freestyle project**, and click **OK**.

2. **Configure Source Code Management:**
   - Under the **Source Code Management** section, select **Git**.
   - Enter the repository URL of your Java project.

3. **Configure Build Triggers (Optional):**
   - Under the **Build Triggers** section, you can select options such as **Poll SCM** to trigger builds based on changes in the repository.

4. **Add Build Step:**
   - Under the **Build** section, click **Add build step**.
   - Select **Invoke top-level Maven targets**.
   - In the **Goals** field, enter `clean package`.

### Step C: Running the Freestyle Job
1. **Save the Job Configuration:**
   - Click **Save** to save the job configuration.

2. **Trigger the Job:**
   - Go to the Jenkins dashboard and select your Freestyle job.
   - Click **Build Now** to trigger the job.

3. **Monitor the Build:**
   - Click on the build number to view the build details.
   - Monitor the console output to ensure that the stages are executed successfully.

### Step D: Verify the Build Results
1. **Check the Workspace:**
   - Go to the build page and click on **Workspace**.
   - Verify that the `target` directory contains the compiled JAR file.

2. **Check the Artifacts:**
   - Go to the **Pipeline** job > **Build History** > **Artifacts** to download and verify the JAR file.

## Final File
Ensure the Freestyle job is successfully set up and the JAR file is generated. Create a document listing:
- The URL of the Git repository containing the Java project.
- A screenshot of the Jenkins Freestyle job execution showing the successful build.
- A screenshot of the generated JAR file in the workspace.

## Summary
In this lab, students learned how to create a Freestyle job in Jenkins to build a Java project using Maven. They configured the job to check out code from a Git repository, build the project, and verify the build results. This lab provided hands-on experience with Jenkins Freestyle jobs and basic build automation for Java projects.