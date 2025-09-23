pipeline {
    agent any

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
post{
success{
    bat 'echo "the build successful"'
}
    failure{
        bat 'echo "build failed"'
    }
}
}
