pipeline {
    agent {
        node {
            label 'Agent01'
        }
    }

    tools {
        jdk 'jdk17.0'
    }
    
    environment {
        APP_NAME = "pdp-pep-testing"
        BRANCH_NAME = "main"
    }

    stages {
        stage('Compile') {
            steps {
                dir('demo') {
                    sh 'java -version'
                    sh 'echo "JAVA_HOME=$JAVA_HOME"'
                    sh './gradlew clean'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('demo') {
                    echo 'Running Tests...'
                    sh 'sudo ./gradlew test --tests "com.example.demo.DemoApplicationConnectorToken" -i'
                }
            }
        }
        }
    }
