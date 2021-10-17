pipeline {
    agent { label 'master'}
    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub-feruza')
    }

    stages {
        stage ('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:frustamova96/jenkins-dockerhub.git'
    }
}

        stage ('Build') {
            steps {
                sh 'docker build -t devops14:latest'
            }
        }

        stage ('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage ('imageTag') {
            steps {
                sh 'docker tag devops14:latest frustamova96/devops114-docker:version2'
            }
        }

        stage ('Push') {
            steps {
                sh ' docker push frustamova96/devops114-docker:version2'
            }
        }  
    }

    post {
        always {
            sh 'docker logout'
        }
    }
}
