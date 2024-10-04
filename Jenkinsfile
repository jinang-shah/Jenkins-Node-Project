pipeline{
    agent any
    tools {nodejs "node"}
    stages {
        stage('Clone Repository'){
            steps{
                git branch: 'master',
                    url: 'https://github.com/jinang-shah/jenkins-node-project.git'
            }
        }
        stage('Install Dependencies'){
            steps {
                sh 'npm install'
            }
        }
         stage('Install pm2'){
            steps {
                sh 'npm install pm2 -g'
            }
        }
        stage('Deploy'){
            steps {
                sh 'pm2 startOrRestart pm2.config.json'
            }
        }
    }
}