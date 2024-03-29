pipeline {
    agent any // window agent, Jenkins-laravel (other machine)
    tools {
            maven 'maven'
    }
    environment {
        BOT_TOKEN = "6853243184:AAF2zVn5Q_bWzgjmAERZjLJp-WEVfMczzDA"
        CHAT_ID = "-1002012810646"
    }
    stages {
        stage('Fetch from GitHub') { //build steps
            steps {
                echo 'Fetching for GitHub'
                git branch: 'Maven', url: 'https://github.com/Monopich/DevOps_All_Project.git'
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            }
        stage ('Deploy') {
            steps {
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
    