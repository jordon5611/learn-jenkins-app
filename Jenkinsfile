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
                    ls -asl
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -asl
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'test -f build/index.html'
            }
        }
    }
}
