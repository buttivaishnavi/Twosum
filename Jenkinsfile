pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                dir('Twosum2') {   
                    script {
                        sh 'javac Twosum.java'
                        sh 'java Twosum'
                    }
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                dir('Twosum2') {   
                    junit 'target/surefire-reports/*.xml'
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build and archive completed successfully!'
        }
        failure {
            echo '❌ Build failed. Please check logs.'
        }
    }
}
