pipeline {
    agent any  // Runs the pipeline on any available agent

    environment {
        MY_VAR = "Hello from Jenkins!"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Your build command here, e.g.:
                sh 'make build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'make test'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'  // Only deploy from main branch
            }
            steps {
                echo 'Deploying application...'
                sh './deploy.sh'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
        always {
            echo 'Cleaning up...'
            cleanWs()  // Clean workspace
        }
    }
}
