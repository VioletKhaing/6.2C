pipeline {
    agent any
    tools {
        maven 'Maven 3.9.4'
    }
    stages {
        stage('Build') {
            steps {
              echo "Using Maven to build the project."
                
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Using Maven for Unit and Integration Tests"
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Using SonarQube for Code Analysis"
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo "Using Owasp Zap for security scan"
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a staging server"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to a production server"
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Sending notifications...'
            emailext(
                subject: 'Jenkins Pipeline - Success',
                body: 'Your Jenkins pipeline has succeeded. No further details are provided.',
                to: 'violetstyles1999@gmail.com'
            )
        }
        failure {
            echo 'Pipeline failed! Sending notifications...'
            emailext(
                subject: 'Jenkins Pipeline - Failure',
                body: 'Your Jenkins pipeline has failed. Please review the build logs for details.',
                to: 'violetstyles1999@gmail.com'
            )
        }
    }
