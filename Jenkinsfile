pipeline{
    agent any 
    
    tool{
        maven "MAVEN"
    }

    environment{
        DOCKER_IMAGE: rukevweubio/web-application
        DOCKER_TAG: latest 
        DOCKER_CREDENTAIL_ID: docker_hub
        GIT_BRANCH: main
        KUBE_CONFIG_CREDENTIALS_ID = 'kube-config-credentials' 
        KUBE_NAMESPACE = 'default' // Adjust as necessary
        SONARQUBE_URL = 'http://your-sonarqube-url' 
        SONARQUBE_TOKEN = credentials('sonarqube-token') 
        GIT_BRANCH = 'feature-branch' 
    }

    stages{
        stage(Checkout){
            steps{
                git branch : "${GIT_BRANCH}", url: "https://github.com/rukevweubio/Jenkins-Maven-Docker-ECR-Pipeline"
            }
        }
           
        stage("maven build the web application" ){
            steps{
                script{
                    sh" maven clean package --Detestskip"
                }
            }
        }

        stage("mavne test " ){
            steps{
                script{
                    sh" maven test"
                }
            }
        }
    }
}
