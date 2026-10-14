pipeline {
    agent any

    environment {
        APP_NAME = 'jenkins-lab'
        ENVIRONMENT = 'production'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/dhruvjuneja100/jenkins-lab.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run') {
            steps {
                sh 'java -jar target/jenkins-lab-1.0.jar'
            }
        }

        stage('Environment Info') {
            steps {
                echo "Application: ${APP_NAME}"
                echo "Environment: ${ENVIRONMENT}"
                echo "Build Number: ${BUILD_NUMBER}"
                echo "Workspace: ${WORKSPACE}"
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }

        failure {
            echo 'Build failed!'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}
