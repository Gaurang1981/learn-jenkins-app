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
                sh 'npm run build'
                sh 'ls -la'
                sh 'npx playwright --version'
            }
        }
        /* stage('Test') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.60.0-noble'
                    reuseNode true
                }
            }
            steps {
                sh 'npx playwright test --reporter=html'
            } */
        }
    }
}