pipeline {
    agent any

    environment {
        IMAGE_NAME = 'netcoredevops'          // Name of your Docker image
        IMAGE_TAG = 'latest'             // Tag for your Docker image
        CREDENTIALS_ID = 'Noob_on_Jenkins'  // Your Jenkins credentials ID
        REPOSITORY_URL = 'https://github.com/bi12-335-usth/.Netcore-DevOps.git'  // URL of your Git repository
        BRANCH_NAME = 'master'          
    }

    stages {
        stage('Checkout from SCM') {
            steps {
                git branch: "${master}", credentialsId: "${Noob_on_Jenkins}", url: "${https://github.com/bi12-335-usth/.Netcore-DevOps.git}"
                // When using Jenkinsfile on another server, user needs to clone their repo before doing so that the server could read the codes
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def dockerfilePath = 'Dockerfile'
                    def customImage = docker.build("${netcoredevops}:${latest}")
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    def customImage = docker.image("${netcoredevops}:${latest}")
                    customImage.run("-p 9000:80") // Adjust ports as necessary
                }
            }
        }
    }
}
