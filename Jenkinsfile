pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-11-openjdk'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-repo/project.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'javac -d out src/*.java'
            }
        }

        stage('Test') {
            steps {
                sh 'java -cp out org.junit.runner.JUnitCore MyTestClass'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'out/**/*.class', fingerprint: true
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to production...'
                // Add deployment script or command here
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
