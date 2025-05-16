pipeline {
    agent any

    environment {
        IMAGE = 'maven:3.8.5-openjdk-17'
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
                    echo '''
                    docker run --rm -v %cd%:/app -w /app maven:3.8.5-openjdk-17 mvn clean package -DskipTests
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo '''
                    docker run --rm -v %cd%:/app -w /app maven:3.8.5-openjdk-17 mvn test
                    '''
                }
            }
        }
    }
}