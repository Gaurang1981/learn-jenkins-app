pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'ls -la'
                sh 'npm ci'
                sh 'npm install -D wait-on'
                sh 'npm run build'
                sh 'npm start &'
                
                sh 'npx playwright --version'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.39.0-jammy'
                    reuseNode true
                }
            }
            steps {
                sh 'npx playwright test --reporter=html'
            } 
        }
    }
}