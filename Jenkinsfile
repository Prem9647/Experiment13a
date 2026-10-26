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

        stage('Deploy') {
            steps {
                echo 'Deploying Python Application...'
                sh '''
                    mkdir -p deployed
                    cp app.py deployed/
                    python3 deployed/app.py > deployed/output.txt
                    cat deployed/output.txt
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline Completed Successfully!'
            archiveArtifacts artifacts: 'deployed/**'
        }

        failure {
            echo 'CI/CD Pipeline Failed!'
        }
    }
}
