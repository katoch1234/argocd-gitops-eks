pipeline {
    agent {
        label 'jenkins-agent'
    }

    environment{
        IMAGE_NAME = "myapp"
        AWS_ACCOUNT_ID = "595496445232"
        AWS_REGION = "us-east-1"
        IMAGE_REPO_NAME = "vaibhav"
        IMAGE_TAG = "${BUILD_NUMBER}"
        REPOSITORY_URL = "595496445232.dkr.ecr.us-east-1.amazonaws.com/vaibhav"
        ECR_REPO_NAME = "vaibhav"
    }

    stages{
        stage('git checkout') {
            steps{
                git branch: 'main', credentialsId: 'github', url:'https://github.com/katoch1234/argocd-gitops-eks.git'
            }
        }

        stage('docker build') {
            steps{
                script{
                     app = docker.build("${IMAGE_NAME}")
                }
        }
        }

        stage ('Logging to ECR') {
            steps {
                script {
                    sh "whoami"
                    sh "aws ecr get-login-password --region ${AWS_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.us-east-1.amazonaws.com"
                }
            }
        }
        stage ('Docker Push') {
            steps {
                script{
                sh "docker tag ${IMAGE_NAME}:latest 595496445232.dkr.ecr.us-east-1.amazonaws.com/vaibhav:${BUILD_NUMBER}"
                sh "docker push 595496445232.dkr.ecr.us-east-1.amazonaws.com/vaibhav:${BUILD_NUMBER}"
            }
            }
        }

        }
}