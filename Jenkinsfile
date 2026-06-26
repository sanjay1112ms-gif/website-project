pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sanjay1112ms-gif/website-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t website:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                sudo docker stop website-container || true
                sudo docker rm website-container || true
                '''
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'sudo docker run -d -p 8080:80 --name website-container website:v1'
            }
        }
    }
}
