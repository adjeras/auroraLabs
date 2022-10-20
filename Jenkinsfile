pipeline {
    
    agent any

    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }
   
    stages {
        
        stage ('Create Helm Package') {
            steps {
                script {
                    dir('/var/jenkins_home/workspace/auroraLabs'){
                        //sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                        sh "docker images"
                        sh "pwd"
                        sh "docker build -t adjeras/auroralabs:latest ."
                    }
                }
            }
        }
        
        stage ('Docker login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage ('Docker push') {
            steps {
                sh "docker push adjeras/auroralabs:latest"
                sh "docker stop auroraApp || echo 'Skipping as the auroralabs container is already stopped'"
                sh "docker rm auroraApp"
                sleep 5
                sh "docker run -p 5000:5000 -id --name auroraApp -v auroralabs_aurora_data:/data adjeras/auroralabs:latest"
            }
        }
/*
        stage ('Installthe latest Helm chart on the AKS cluster') {
            steps {
                script {
                    sh "helm repo update"
                    sleep 5
                    sh "helm search repo my-helm-charts -l --devel"
                    sh "helm repo update"
                    sleep 5
                }
            }
        }
*/
    }
}
