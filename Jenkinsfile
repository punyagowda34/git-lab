pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                sh 'mkdir -p build'
                sh 'javac -d build Main.java'
            }
        }

        stage('Test') {
            steps {
                sh 'java -cp build Main'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build/*.class', fingerprint: true
            }
        }
    }

    post {
        success { echo 'Pipeline success!' }
        failure { echo 'Pipeline failed!' }
    }
}
