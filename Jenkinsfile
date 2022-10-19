pipeline {
    
    agent any
   
    stages {
        
        stage ('Create Helm Package') {
            steps {
                script {
                    //sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                    sh "docker images"
                    sh "pwd"
                    /*dir('/var/lib/jenkins/workspace'){
                        //sh "git clone git@github.com:adjeras/my-helm-charts.git"
                    }
                    dir('/var/lib/jenkins/workspace/helmDeploy/my-helm-charts'){
                        sh "sed -i 's/version:.*/version: 0.1.${env.BUILD_ID}/g' Charts/simplewebapp/Chart.yaml"
                        sh "helm package Charts/simplewebapp"
                        sh "mv simplewebapp-0*.tgz ~/workspace/my-helm-charts/Packages/"
                        sh "helm repo index ~/workspace/my-helm-charts/"
                    } */
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

        /* stage ('Installthe latest Helm chart on the AKS cluster') {
            steps {
                script {
                    sh "helm repo update"
                    sleep 5
                    sh "helm search repo my-helm-charts -l --devel"
                    sh "helm repo update"
                    sleep 5
                }
            }
        } */
    }
}
