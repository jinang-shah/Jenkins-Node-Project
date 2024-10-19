pipeline{
    agent any
    tools {nodejs "node"}
    stages {
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
        stage('Install Dependencies'){
            steps{
                sh 'npm install'
            }
        }
        stage('Build'){
            steps {
                sh 'npm run build'
            }
        }
        stage('Build Image'){
            steps {
                sh 'docker build -t  my-node--app:1.0 .'
            }
        }
        stage('Push to Docker Registry'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker_cred', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]){
                    sh 'echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin'
                    sh 'docker tag my-node-app:1.0 jinangshah/node-docker-jenkins:1.0'
                    sh 'docker push jinangshah/node-docker-jenkins:1.0'
                    sh 'docker logout'
                }
            }
        }
        
    }
}