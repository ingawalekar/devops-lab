pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh '''
                echo "Building Docker Image"
                docker build -t ganesh-web:latest .
                '''
            }
        }

        stage('Verify Kubernetes Access') {
            steps {
                sh '''
                kubectl --kubeconfig=/var/jenkins_home/.kube/config get pods
                '''
            }
        }

        stage('Restart Deployment') {
            steps {
                sh '''
                kubectl --kubeconfig=/var/jenkins_home/.kube/config \
                rollout restart deployment ganesh-web
                '''
            }
        }

        stage('Verify Rollout') {
            steps {
                sh '''
                kubectl --kubeconfig=/var/jenkins_home/.kube/config \
                rollout status deployment/ganesh-web
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Deployment Failed'
        }

        always {
            echo 'Pipeline Finished'
        }
    }
}
