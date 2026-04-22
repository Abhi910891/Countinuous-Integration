pipeline {
    agent any

    stages {

      
        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t myapp .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker stop myapp || true'
                bat 'docker rm myapp || true'
                bat 'docker run -d -p 8000:8000 --name myapp myapp'
            }
        }
    }
}