pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/rxlnj/PES1UG21CS500_Jenkins']]])
            }
        }
        stage('Build') {
            steps {
                sh 'g++ main.cpp -o output'
            }
        }
        stage('Test') {
            steps {
                sh './output'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }
    post {
        always {
            script {
                if (currentBuild.result == 'FAILURE') {
                    echo 'Pipeline failed!'
                }
            }
        }
    }
}
