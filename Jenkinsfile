pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code pulled from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                echo "Building Docker Image"

                docker build -t ganesh-web:latest .

                echo "Available Images"
                docker images | grep ganesh
                '''
            }
        }

        stage('Validation') {
            steps {
                sh '''
                echo "Validating Docker Image"

                docker image inspect ganesh-web:latest > /dev/null

                echo "Image Validation Successful"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Deployment Stage"

                echo "Build completed successfully"

                echo "Ready for Kubernetes deployment"
                '''
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        always {
            echo 'Pipeline execution finished'
        }
    }
}
