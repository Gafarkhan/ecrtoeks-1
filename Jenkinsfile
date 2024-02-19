pipeline {
    agent any
    environment {
        AZURE_CREDENTIALS_ID = '17fef5c7-28b5-4d62-9b28-bae46e0a8830'
        AZURE_RESOURCE_GROUP = 'Chirala-rg'
        AZURE_LOCATION = 'uksouth'
        
    }

    stages {
        stage('Deploy to Azure') {
            steps {
                script {
                    azureCLI(
                        credentialsId: env.17fef5c7-28b5-4d62-9b28-bae46e0a8830,
                        subscriptionId: 'your-azure-subscription-id',
                        scriptLocation: 'https://github.com/Gafarkhan/ecrtoeks-1/blob/master/Dockerfile',
                        executeCommands: true
                    )
                }
            }
        }
    }
}


    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Gafarkhan/ecrtoeks-1']])
            }
        }
        
        stage('acr login') {
            steps {
                sh 'az acr login --name myacr2022.azurecr.io --region uk-south | docker login --username gafar22 --password-9398333455@Gk.uk-south'
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
