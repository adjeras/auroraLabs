pipeline {
    
    agent any
   
    stages {
        
        stage ('Create Helm Package') {
            steps {
                script {
                    //sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                    sh "docker images"
                    sh "pwd"
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
