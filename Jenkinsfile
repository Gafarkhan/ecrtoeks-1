pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Gafarkhan/ecrtoeks-1']])
            }
        }
        
        stage('acr login') {
            steps {
                sh 'az acr login --name myacr2022.azurecr.io'
            }
        }
        
        stage('docker build') {
            steps {
                sh 'Docker build -t nginx:v1 .'
            }
        }
        
        stage('Tag') {
            steps {
                sh 'docker tag nginx:v1 gafar22/docker/nginx:v1'
            }
        }
        
        stage('Docker push'){
            steps {
                sh 'docker gafar22/docker/nginx:v1'
            }
        }
        
        // stage('deploy to eks'){
        //     steps {
        //         sh 'kubectl get nodes'
                
        //         sh 'kubectl get all'
                
        //         sh 'kubectl apply -f webapp.yaml'
                
        //         sh 'kubectl get pods'
                
        //         sh 'kubectl get all'
        //     }
        // }
        
    }
}
