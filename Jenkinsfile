pipeline {
    agent any // You may specify the agent/machine as per your requirement
    environment {
        BOT_TOKEN = "6853243184:AAF2zVn5Q_bWzgjmAERZjLJp-WEVfMczzDA"
        CHAT_ID = "-1002012810646"
    }
    stages {
        stage('Fetch from GitHub') { // Build steps
            steps {
                echo 'Fetching from GitHub'
                git branch: 'tp2', url: 'https://github.com/Monopich/devops_jenkins.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building the project..."
                sh "./mvnw clean install -DskipTests"
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                sh "./mvnw test -Punit"
            }
        }
        stage('Deployment') {
            steps {
                echo "Deploying the artifact..."
                sh './mvnw spring-boot:run -Dserver.port=8001 &'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the artifact..."
                bat "mvn jar:jar deploy:deploy"
            }
        }
    }
    post {
        success {
            script {
                sh 'sh 1-success-deploy.sh'
            }
        }
        failure {
            script {
                sh 'sh 2-fail-deploy.sh'
            }
        }
    }
}
