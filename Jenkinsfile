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
                git branch: 'tp2', url: 'https://github.com/Monopich/devops_jenknis.git'
            }
        }
       stages {
            stage('Build'){
                steps {
                    echo "Building the project..."
                    bat "mvn clean install -DskipTests"
                }
            }

            stage('Test'){
                steps{
                    echo "Running tests..."
                    bat "mvn test"
                }
            }

            stage('Deploy') {
                steps {
                    echo "Deploying the artifact..."
                    bat "mvn jar:jar deploy:deploy"
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
    