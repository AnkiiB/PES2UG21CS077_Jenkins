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
                sh 'make -C main' // Run Makefile to compile hello.cpp
            }
        }
        stage('Test') {
            steps {
                sh './main/hello' // Assuming hello.cpp generates an executable named 'hello'
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
