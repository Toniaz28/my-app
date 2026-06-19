# Jenkins CI/CD Pipeline Project

## Project Overview

This project demonstrates the implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins. The goal of the project is to automate the software development workflow by integrating source control, build automation, testing, and deployment stages into a single pipeline.

The pipeline is configured using the Pipeline-as-Code approach through a Jenkinsfile stored in the root directory of the repository.

---

## Objectives

* Understand the principles of Continuous Integration (CI)
* Set up and configure Jenkins automation server
* Integrate Jenkins with GitHub
* Automate application build and testing processes
* Implement a Declarative Jenkins Pipeline
* Simulate application deployment
* Monitor pipeline execution through Jenkins dashboard

---

## Technologies Used

* Jenkins
* Git & GitHub
* Java
* Maven
* JUnit
* Ubuntu Linux

---

## Project Structure

```bash
my-app/
│
├── src/
├── tests/
├── pom.xml
├── Jenkinsfile
└── README.md
```

---

## Jenkins Pipeline Stages

The pipeline consists of the following stages:

### 1. Clone Stage

Fetches the latest source code from the GitHub repository.

### 2. Build Stage

Compiles the application using Maven.

```bash
mvn clean compile
```

### 3. Test Stage

Executes automated unit tests.

```bash
mvn test
```

### 4. Package Stage

Packages the application into a deployable artifact.

```bash
mvn package
```

### 5. Deploy Stage

Simulates deployment to a test environment.

---

## Jenkinsfile

The pipeline is defined using a Declarative Jenkins Pipeline.

Example:

```groovy
pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying application..."'
            }
        }
    }
}
```

---

## Jenkins Setup Process

### Step 1: Install Java

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

### Step 2: Install Jenkins

Follow the official Jenkins installation guide.

Start Jenkins service:

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Step 3: Install Required Plugins

The following plugins were installed:

* Git Plugin
* Pipeline Plugin
* Maven Integration Plugin
* GitHub Integration Plugin

### Step 4: Configure Maven

Navigate to:

```text
Manage Jenkins → Global Tool Configuration
```

Add Maven installation and enable automatic installation.

---

## GitHub Integration

The Jenkins pipeline is connected to a GitHub repository using Git integration.

Automatic builds can be triggered using:

* GitHub Webhooks
* Poll SCM

---

## Running the Pipeline

1. Open Jenkins Dashboard
2. Create a new Pipeline project
3. Configure GitHub repository
4. Select “Pipeline script from SCM”
5. Build the project

Successful execution shows all stages in green.

---

## Challenges Encountered

### Maven Not Found

The pipeline initially failed because Maven was not configured in Jenkins tools.

**Solution:**
Configured Maven in Jenkins Global Tool Configuration.

### Git Authentication Issues

Jenkins was unable to access the GitHub repository.

**Solution:**
Configured repository access using GitHub credentials.

### Test Failures

Some tests failed during pipeline execution.

**Solution:**
Executed tests locally before pushing changes to GitHub.

---

## Screenshots

Include screenshots of:

* Jenkins Dashboard
* Successful Pipeline Execution
* Console Output Logs
* Green Build/Test/Deploy Stages

---

## Conclusion

This project demonstrates how Jenkins can automate software integration workflows through CI/CD pipelines. By implementing automated builds, testing, and deployment stages, the project improves development efficiency, consistency, and software quality.

---

## References

* Jenkins Documentation
* Maven Documentation
* GitHub Documentation
