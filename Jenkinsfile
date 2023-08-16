pipeline {
    agent {
        docker {
            image 'node:18.17.1-alpine3.18'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm run test/serverTest.js'
            }
        }
        stage('Deliver') { 
            post {
            success {
                slackSend "Build deployed successfully - ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
            }
        } 

    }
}
    
