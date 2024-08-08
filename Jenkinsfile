pipeline {
    agent {
        label: 'jenkins-agent'
    }

    stages{
        stage('git checkout') {
            steps{
                git branch: 'main', credentialsId: 'github', url:'https://github.com/katoch1234/argocd-gitops-eks.git'
            }
        }
    }
}