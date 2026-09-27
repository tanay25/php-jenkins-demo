pipeline {
    agent any

    stages {
        stage('Checkout'){
            steps {
                git branch: main, url: ''
            }
        }
        stage('Build Docker'){
            steps {
                sh 'docker build -t php-jenkins-demo:latest .'
            }
        }
        stage('Run Container'){
            steps{
                sh '''
                    docker rm -f php-demo || true
                    docker run -d --name php-demo -p 8080:80 php-jenkins-demo:latest
                '''
            }
        }
    }
}