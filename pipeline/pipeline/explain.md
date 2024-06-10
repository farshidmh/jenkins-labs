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

### Explanation

#### Pipeline Block
```groovy
pipeline {
```
- The `pipeline` block defines the entire pipeline script. Everything within this block is part of the pipeline.

#### Agent Directive
```groovy
    agent any
```
- The `agent` directive specifies where the pipeline or a specific stage runs. `any` means the pipeline can run on any available agent.

#### Tools Directive
```groovy
    tools {
        jdk 'Default'
        maven 'Default'
    }
```
- The `tools` directive specifies the tools needed for the pipeline. Here, it declares the use of the JDK and Maven, with 'Default' referring to the default installation names configured in Jenkins.

#### Stages Block
```groovy
    stages {
```
- The `stages` block contains a series of stages that define the build process.

#### Checkout Stage
```groovy
        stage('Checkout') {
            steps {
                git 'https://github.com/your-repo/JenkinsfileJavaProject.git'
            }
        }
```
- The `Checkout` stage checks out the source code from the specified Git repository.
- `stage('Checkout')`: Defines a stage named "Checkout".
- `steps { ... }`: Contains the steps to be executed in this stage.
- `git 'https://github.com/your-repo/JenkinsfileJavaProject.git'`: Checks out code from the specified Git repository URL.

#### Build Stage
```groovy
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
```
- The `Build` stage compiles the Java project and packages it into a JAR file.
- `stage('Build')`: Defines a stage named "Build".
- `steps { ... }`: Contains the steps to be executed in this stage.
- `sh 'mvn clean package'`: Runs the Maven command to clean the project and build the package.

#### Test Stage
```groovy
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
```
- The `Test` stage runs the unit tests for the Java project.
- `stage('Test')`: Defines a stage named "Test".
- `steps { ... }`: Contains the steps to be executed in this stage.
- `sh 'mvn test'`: Runs the Maven command to execute the tests.

#### Archive Stage
```groovy
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
```
- The `Archive` stage archives the built JAR file for later retrieval.
- `stage('Archive')`: Defines a stage named "Archive".
- `steps { ... }`: Contains the steps to be executed in this stage.
- `archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true`: Archives the JAR files found in the `target` directory. `**/target/*.jar` is a pattern matching all JAR files in the `target` directory, and `fingerprint: true` creates a fingerprint of the artifacts for tracking.

#### Post Block
```groovy
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
```
- The `post` block defines actions to be taken after the pipeline or a specific stage completes.
- `post { ... }`: Contains the post conditions.
- `success { ... }`: Defines steps to run if the pipeline succeeds.
  - `echo 'Pipeline completed successfully!'`: Prints a success message.
- `failure { ... }`: Defines steps to run if the pipeline fails.
  - `echo 'Pipeline failed.'`: Prints a failure message.