pipeline{

    agent any

    environment{
        dockerImage = ''
        registry = 'shivmodi1203/jenkins_docker'
    }

    stages{
        stage('Build Docker Image'){
            steps{
                dockerImage = docker.build registry
            }
        }
    }
}