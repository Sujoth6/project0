
pipeline {
    agent any

    triggers {
        pollSCM('* * * * *') // Polls every minute
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the app'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the app'
            }
        }
    }
}
