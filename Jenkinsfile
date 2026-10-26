pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Python Application...'
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Python Application...'
                sh 'python3 -m unittest discover -v'
            }
        }
    }

    post {
        success {
            echo 'Build and Test Completed Successfully!'
        }

        failure {
            echo 'Pipeline Failed!'
        }
    }
}
