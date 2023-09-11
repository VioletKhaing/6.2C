pipeline {
    agent any
    tools {
        maven 'Maven 3.9.4'
    }
    stages {
        stage('Build') {
            steps {
                
                // Build the code using a build automation tool (e.g., Maven)
                sh 'mvn clean package'
                
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests to ensure the code functions as expected
                sh 'mvn test'

                // Run integration tests to verify component interaction
                sh 'mvn integration-test'
            }
        }

        stage('Code Analysis') {
            steps {
                // Run code analysis using SonarQube
                withSonarQubeEnv('SonarQubeServer') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Security Scan') {
            steps {
                // Perform a security scan using OWASP ZAP
                sh 'owasp-zap-scan.sh -t http://your-app-url'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                sh 'deploy-to-staging.sh'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                sh 'mvn integration-test -Denvironment=staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                sh 'deploy-to-production.sh'
            }
        }
    }

    post {
        success {
            // Send a notification on successful pipeline execution
            echo 'Pipeline succeeded! Sending notifications...'
            emailext(
                subject: 'Jenkins Pipeline - Success',
                body: 'Your Jenkins pipeline has succeeded. No further details are provided.',
                to: 'violetstyles1999@gmail.com'
            )
        }
        failure {
            // Send a notification on pipeline failure
            echo 'Pipeline failed! Sending notifications...'
            emailext(
                subject: 'Jenkins Pipeline - Failure',
                body: 'Your Jenkins pipeline has failed. Please review the build logs for details.',
                to: 'violetstyles1999@gmail.com'
            )
        }
    }
}
