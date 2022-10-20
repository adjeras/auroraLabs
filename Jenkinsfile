pipeline {
    
    agent any
   
    stages {
        
        stage ('Create Helm Package') {
            steps {
                script {
                    dir('/var/jenkins_home/workspace/auroraLabs'){
                        //sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                        sh "docker images"
                        sh "pwd"
                        sh "docker build -t adjeras/auroralabs:latest ."
                        sh "docker stop auroraApp || docker run -p 5000:5000 -id --name auroraApp -v auroralabs_aurora_data:/data adjeras/auroralabs:latest "
                    }
                }
            }
        }
        
        stage ('Push Helm chart to my-helm-charts repo') {
            steps {
                script {
                    dir('/var/lib/jenkins/workspace/'){
                        sh "pwd"
                    }
                    sleep 50
                }
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
