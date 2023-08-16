pipeline {
    agent {
        docker {
            image 'node:18.17.1-alpine3.18'
            args '-p 3000:3000'
        }
    }
    tools {nodejs "node"}

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'node test'
            }
        }

//         stage('deploy') {
//             steps {
//                 sh ''
//             }
        }
        stage('Deliver') {
            post {
            success {
                slackSend "Build deployed successfully - ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
            }
        } 

    }
}
    
