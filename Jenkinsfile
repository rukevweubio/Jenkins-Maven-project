pipeline {
    agent any

    tools {
        maven "MAVEN"   // Must match Jenkins Maven tool configuration
       
    }

    environment {
        DOCKER_IMAGE = "rukevweubio/web-application"
        DOCKER_TAG = "latest"
        DOCKER_CREDENTIAL_ID = "docker_hub"
        GIT_BRANCH = "feature-branch"
        KUBE_CONFIG_CREDENTIALS_ID = "kube-config-credentials"
        KUBE_NAMESPACE = "default"
        SONARQUBE_URL = "http://your-sonarqube-url"
        SONARQUBE_TOKEN = credentials("sonarqube-token")
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${GIT_BRANCH}", url: "https://github.com/rukevweubio/Jenkins-Maven-Docker-ECR-Pipeline.git"
            }
        }

        stage('Maven Build the Web Application') {
            steps {
                script {
                    sh "mvn clean package -DskipTests"
                }
            }
        }

        stage('Maven Test') {
            steps {
                script {
                    sh "mvn test"
                }
            }
        }
    }
}
