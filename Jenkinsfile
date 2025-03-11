pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }
    stages {
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
            
            steps {
                sh '''
                    echo "Test stage"
                    ls -la
                    if test -f build/index.html; then
                        echo "File exists"
                    fi
                    npm test
                '''
            }
        }
    }
}
