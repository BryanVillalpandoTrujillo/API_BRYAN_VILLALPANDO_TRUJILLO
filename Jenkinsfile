pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/BryanVillalpandoTrujillo/API_BRYAN_VILLALPANDO_TRUJILLO.git'
            } 
        }
        stage('Build') {
            steps {
                sh 'docker build -f WebAPINET8/Dockerfile -t bryan134554/counter-image-api:latest .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([string(credentialsId: 'Jenkins-docker', variable: 'DOCKER_LOGIN')]) {
                    sh "docker login -u bryan134554 -p ${DOCKER_LOGIN}"
                }
                sh 'docker push bryan134554/counter-image-api:latest'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker run -d -p 8081:8081 -p 8082:8082 bryan134554/counter-image-api:latest'
                }
            }
        }
        // Otras etapas del pipeline...
    }
}