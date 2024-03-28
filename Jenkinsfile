pipeline {
    agent any // window agent, Jenkins-laravel (other machine)
    environment {
        BOT_TOKEN = "6853243184:AAF2zVn5Q_bWzgjmAERZjLJp-WEVfMczzDA"
        CHAT_ID = "-1002012810646"
    }
    tools {
            maven "maven 3.9.2"
    }
    stages {
        stage('Fetch from GitHub') { //build steps
            steps {
                echo 'Fetching for GitHub'
                git branch: 'Maven', url: 'https://github.com/Monopich/DevOps_All_Project.git'
            }
        }
        stage('Build using Tools'){
            steps{
                echo 'Compiling code ...'
                sh 'mvn install'
                sh 'mvn clean package'
            }
        }
        stage('Test the app'){
            steps{
                echo 'Testing unit tests...'
                echo 'Testing feature...'
                sh 'java -cp target/mytp01-1.0-SNAPSHOT.jar gic.demo.App'
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
    