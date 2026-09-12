pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
    success {
        emailext(
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "The Jenkins CI pipeline completed successfully.",
            to: "dasarimeghamala.23.cse@anits.edu.in"
        )
    }
    failure {
        emailext(
            subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "The Jenkins CI pipeline failed. Please check the Jenkins console output.",
            to: "dasarimeghamala.23.cse@anits.edu.in"
        )
    }
}}