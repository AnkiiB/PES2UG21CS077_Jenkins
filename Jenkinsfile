pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/AnkiiB/PES2UG21CS077_Jenkins.git']]])
            }
        }
        stage('Build') {
            steps {
                build 'PES2UG21CS077-1'
                sh 'g++ main/hello.cpp -o output'
            }
        }
        stage('Test') {
            steps {
                sh './output'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    try {
                        echo 'Deployment steps...'
                        // Intentional error: Force a failure in the deploy stage
                        error 'Deploy failed'
                    } catch (Exception e) {
                        echo "Caught an exception: ${e.getMessage()}"
                    }
                }
            }
        }
    }
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
