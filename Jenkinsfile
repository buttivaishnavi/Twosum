pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'echo Building Twosum app...'
                bat 'javac Twosum.java'
            }
        }

        stage('Test / Run') {
            steps {
                bat 'echo Running Twosum...'
                bat 'java Twosum'
            }
        }
    }
}

