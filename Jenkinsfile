pipeline{

    agent any

    environment{
        dockerImage = ''
        registry = 'shivmodi1203/jenkins_docker_image'
    }

    stages{
        stage('Build Docker Image'){
            steps{
                script{
                    dockerImage = docker.build("${registry}:latest")
                }
            }
        }
    }
}