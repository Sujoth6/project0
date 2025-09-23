pipeline {
    agent any

    stages {
        stage('Checkout code') {
            steps {
                git 'https://github.com/Sujoth6/project0'
            }
        }
        stage('Build') {
            steps {
                sh 'echo Building the project'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Running tests'
            }
        }
        stage('Verifying') {
            steps {
                sh 'echo Verifying the test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploying application'
            }
        }
    }
}
