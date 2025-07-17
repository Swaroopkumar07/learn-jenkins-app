pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo 'before Installation'
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                echo 'after Installtion'
                ls -la

                '''
               
            }
        }
        stage('Test') {
            steps {
                sh '''
                echo 'testing stage'
                test -f build/index.html
                npm test
                

                '''
               
            }
        }
    }
}
