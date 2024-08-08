pipeline {
    agent {
        label 'jenkins-agent'
    }

    environment{
        IMAGE_NAME = "myapp"
    }

    stages{
        stage('git checkout') {
            steps{
                git branch: 'main', credentialsId: 'github', url:'https://github.com/katoch1234/argocd-gitops-eks.git'
            }
        }

        stage('docker build') {
                steps{
                    sh "docker build -t myapp:${BUILD_NUMBER} ."
                }
            }
        }
}