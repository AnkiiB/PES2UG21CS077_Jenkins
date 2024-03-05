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
                // Intentional error: Typo in the command
                sh 'cmake .'
            }
        }
        stage('Test') {
            steps {
                sh '''
                ./output
                for i in {1..5}; do
                    echo $i
                done
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
