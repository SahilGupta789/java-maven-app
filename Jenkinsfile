pipeline {
    agent any

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
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn test'
            }
        }

        stage('Cleanup') {
            steps {
                echo "Cleaning up temporary files..."
                sh 'mvn clean'
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
