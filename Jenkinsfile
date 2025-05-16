pipeline {
    agent any

    environment {
        IMAGE = 'anshnaidu/flightbooking:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ansh-naidu/Honours-VI-SEM-Assignment'
            }
        }

        stage('Build') {
            steps {
                script {
                    echo """
                    docker run --rm -v ${pwd()}:/app -w /app ${IMAGE} mvn clean package -DskipTests
                    """
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo """
                    docker run --rm -v ${pwd()}:/app -w /app ${IMAGE} mvn test
                    """
                }
            }
        }
    }
}