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
                // Compile the .cpp file using shell script
                sh 'g++ -o output_file main.cpp'
            }
        }
        stage('Test') {
            steps {
                // Print output of .cpp file using shell script
                sh './output_file'
            }
        }
        stage('Deploy') {
            steps {
                // Add deployment steps here if needed
                echo 'Deployment steps...'
            }
        }
    }
    
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
