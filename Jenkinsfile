pipeline {
    agent any

    stages {

        stage('Kubernetes Access Test') {
            steps {
                sh '''
                kubectl --kubeconfig=/var/jenkins_home/.kube/config get pods
                '''
            }
        }

    }

    post {
        success {
            echo 'Kubernetes Access Successful'
        }

        failure {
            echo 'Kubernetes Access Failed'
        }

        always {
            echo 'Pipeline Finished'
        }
    }
}
