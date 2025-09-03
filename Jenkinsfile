pipeline {
    agent any
    tools {
        jdk 'java 17' 
    }
    stages {
        stage('Checkout') {
            steps {
                echo "Pulling code from Git..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building the application..."
                bat 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                bat 'mvn test'
            }
        }

        stage('Cleanup') {
            steps {
                echo "Cleaning up temporary files..."
                bat 'mvn clean'
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully"
        }
        failure {
            echo "Pipeline failed"
        }
        always {
            echo "Pipeline finished. Cleaning workspace..."
            cleanWs()
        }
    }
}

