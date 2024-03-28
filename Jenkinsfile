pipeline {
    agent any
    environment {
        BOT_TOKEN = "6853243184:AAF2zVn5Q_bWzgjmAERZjLJp-WEVfMczzDA"
        CHAT_ID = "-1002012810646"
    }
    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/Python']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Monopich/DevOps_All_Project.git']])
            }
        }
        stage('build') {
            steps {
                git branch: 'Python', url: 'https://github.com/Monopich/DevOps_All_Project.git' 
                sh 'python3 Python.py'
            }
        }
    }
    post{
            success{
                sh '''
                sh 1-success-deploy.sh;\
                '''
            }
            failure{
                sh '''
                sh 2-fail-deploy.sh;\
                '''
            }
    }
}
