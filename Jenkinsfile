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
        stages {
            stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            }
            stage ('Deploy') {
            steps {
                script {
                deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://dayal-test.letspractice.tk:8081')], contextPath: '/pipeline', onFailure: false, war: 'webapp/target/*.war' 
                }
            }
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
    