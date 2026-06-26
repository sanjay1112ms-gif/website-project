pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t website:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop website-container || true
                docker rm website-container || true
                '''
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name website-container website:v1'
            }
        }
    }
}
