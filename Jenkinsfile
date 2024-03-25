pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/venkykukatla/helm.git']])
            }
        }
        
        stage('helm version') {
            steps {
                sh "helm version --short"
            }
        }
        
        stage('helm lint') {
            steps {
                sh "helm lint myfirsthelm"
            }
        }
        
        stage('helm package') {
            steps {
                sh "helm package myfirsthelm"
            }
        }
        
        stage('deploy to eks') {
            steps {
    
                sh "kubectl get all"  
                sh "helm list"
                // sh "helm install mychart1 myfirsthelm-0.1.0.tgz"
                sh "helm upgrade --install mychart1 myfirsthelm-0.1.0.tgz -f ./myfirsthelm/values.yaml"
                sh "helm list"
                 sh "kubectl get all" 
    // some block
}
}
            
        }
        
        
        
    }
