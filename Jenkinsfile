pipeline {
    agent any

    tools {
        maven 'Maven_3.9.11' // This should match the name you entered in Jenkins Global Tool Config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sanu15/sample_maven_project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        failure {
            echo 'Build or tests failed.'
        }
    }
}
