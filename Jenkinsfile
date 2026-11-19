pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code pulled from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t ganesh-web:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker save ganesh-web:latest -o ganesh-web.tar

                sudo k3s ctr images import ganesh-web.tar
                '''
            }
        }
    }
}
