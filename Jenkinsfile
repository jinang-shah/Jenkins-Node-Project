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
        
    }
}