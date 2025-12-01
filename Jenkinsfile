pipeline {
    agent any

    triggers {
        // Option 1: Poll SCM every minute for new commits
        pollSCM('* * * * *')
        // If you configure a GitHub/GitLab webhook instead, you can remove pollSCM.
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building Twosum app..."'
                sh 'javac Twosum.java'
            }
        }

        stage('Test / Run') {
            steps {
                sh 'echo "Running Twosum..."'
                sh 'java Twosum'
            }
        }
    }
}
