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
                sh 'sudo npm install'
            }
        }
        stage('Build'){
            steps {
                sh 'npm run build'
            }
        }
        
    }
}