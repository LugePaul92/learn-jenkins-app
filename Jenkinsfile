pipeline {
    agent any
    stages {
        agent {
            docker {
                image 'node:18-alpine'
                reuseNode true
            }
        }
        stage('Build') {
            
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Test stage"
                    ls -la
                    if test -f build/index.html; then
                        echo "File index.html exists"
                    fi
                    npm test
                '''
            }
        }
    }
}
