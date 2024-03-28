pipeline {
    agent any // window agent, Jenkins-laravel (other machine)
    environment {
        BOT_TOKEN = "6853243184:AAF2zVn5Q_bWzgjmAERZjLJp-WEVfMczzDA"
        CHAT_ID = "-1002012810646"
    }
    stages {
        stage('Fetch from GitHub') { //build steps
            steps {
                echo 'Fetching for GitHub'
                git branch: 'VueJS', url: 'https://github.com/Monopich/DevOps_All_Project.git'
            }
        }
        stage('Build using Tools'){
            steps{
                echo 'Compiling code ...'
                sh 'npm install'
            }
        }
        stage('Test the app'){
            steps{
                echo 'Testing unit tests...'
                echo 'Testing feature...'
                sh 'npm run build'
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