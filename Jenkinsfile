pipeline{

    agent any

    environment{
        dockerImage = ''
        registry = 'shivmodi1203/jenkins_docker_image'
        registryCredentials = 'Docker'
    }

    stages{
        stage('Build Docker Image'){
            steps{
                script{
                    dockerImage = docker.build("${registry}:${env.BUILD_ID}")
                }
            }
        }
        stage('Push Docker Image'){
            steps{
                script{
                    docker.withRegistry('', registryCredentials){
                        dockerImage.push()
                    }
                }
            }
        }
        stage('Deploy Container'){
            steps{
                script{
                    docker.withRegistry('', registryCredentials){
                        def runContainer = docker.image("${registry}:${env.BUILD_ID}").run('--name mynew-container -d')
                        echo "Container ID: ${runContainer.id}"
                    }
                }
            }
        }
    }
}