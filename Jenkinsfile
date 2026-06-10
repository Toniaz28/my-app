#!/bin/bash

pipeline {
agent any

```
stages {

    stage('Clone Repo') {
        steps {
            sh 'git clone https://github.com/Toniaz28/my-app.git'
        }
    }

    stage('Clean') {
        steps {
            dir('my-app') {
                sh 'mvn clean'
            }
        }
    }

    stage('Test') {
        steps {
            dir('my-app') {
                sh 'mvn test'
            }
        }
    }

    stage('Package') {
        steps {
            dir('my-app') {
                sh 'mvn package'
            }
        }
    }
}
```

}

