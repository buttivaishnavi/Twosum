pipeline {
    agent any

    tools {
        jdk 'JDK21'     
        maven 'Maven3' 
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('Twosum2') {   
                    script {
                        bat 'mvn clean install'
                    }
                }
            }
        }

        stage('Build & Test') {
            steps {
                dir('Twosum2') {   
                    script {
                        bat 'mvn package'
                        bat 'mvn test'
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
