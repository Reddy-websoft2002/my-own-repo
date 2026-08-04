pipeline {
    agent any

    tools {
        maven 'maven-sonar'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Reddy-websoft2002/saidemytrend.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'sonar-sonar'
            }

            steps {
                withSonarQubeEnv('sonar-sonar') {
                    sh """
                    ${scannerHome}/bin/sonar-scanner \
                    -Dsonar.projectKey=sonar-project \
                    -Dsonar.sources=src \
                    -Dsonar.java.binaries=target/classes
                    """
                }
            }
        }
    }
}
