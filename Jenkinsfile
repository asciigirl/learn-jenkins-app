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
                sh '''
                node --version
                npm --version
                npm ci
                npm run build
                '''
            }
        }
        stage ('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            steps {
                echo "Test stage"
                sh '''
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }
}
