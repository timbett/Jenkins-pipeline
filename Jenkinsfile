pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // dir of the file
                dir('/Jenkins-pipeline') {
                    // Build the code using Maven
                    echo "mvn clean package"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit
                echo "mvn test"

                // Run integration tests
                echo "Run integration tests"
            }
        }

        stage('Code Analysis') {
            steps {
                // Integrate code analysis 
                echo "sonar-scanner"
            }
        }

        stage('Security Scan') {
            steps {
                // Perform security scan using a security scanning tool (e.g., OWASP ZAP)
                echo "zap-cli --quick-scan -t http://localhost:8080"
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy application to a staging server (e.g., AWS EC2)
                echo "aws ec2 deploy <options>"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                echo "mvn integration-test -Denv=staging"
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy application to a production server (e.g., AWS EC2)
                echo "aws ec2 deploy <options>"
            }
        }
    }

    post {
        success {
            // Send notification email on success
            emailext (
                to: 'tkkibat@gmail.com',
                subject: "Pipeline Success",
                body: "Pipeline ran successfully. Check attachment for logs.",
                attachmentsPattern: "**/*"
            )
        }
        failure {
            // Send notification email on failure
            emailext (
                to: 'tkkibet@gmail.com',
                subject: "Pipeline Failure",
                body: "Pipeline failed. Check attachment for logs.",
                attachmentsPattern: "**/*"
            )
        }
    }
}
