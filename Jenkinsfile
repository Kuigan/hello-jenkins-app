pipeline {
    agent any
    
    environment {
        GITHUB_REPO = 'https://github.com/Kuigan/hello-jenkins-app'
    }
    
    stages {
        stage ('Checkout') {
            steps {
                git url: "${GITHUB_REPO}", branch: 'main'
            }
        }
  
        stage ('Build') {
            steps {
                echo 'Building the app...'
                sh 'cat app.txt'
                echo 'Build successful.'
            }
        }
  
        stage ('Test') {
            steps {
                echo 'Testing'
                script{
                        def status = sh(script: 'diff app.txt test.txt', returnStatus: true)
                        if (status != 0) {
                            error('Test failed.')
                        }
                    }
                echo 'Testing seccuessful.'
            }
        }
        
        stage ('Package') {
            steps {
                echo 'Packaging...'
                sh 'tar -cvf app.tar'
                echo 'Packaging successful'
                }
            }
        }
}