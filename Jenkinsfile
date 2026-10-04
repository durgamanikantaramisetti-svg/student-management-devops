pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://' + 'github.com/durgamanikantaramisetti-svg/student-management-devops.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t student-management:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop student-management || true'
                sh 'docker rm student-management || true'
                sh 'docker run -d --name student-management -p 8082:8080 student-management:latest'
            }
        }
    }
}
