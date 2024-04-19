pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'Fastman', contextName: '', credentialsId: 'kubenetes', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://3462B304710E427F469369365B220D6A.gr7.us-east-1.eks.amazonaws.com') { 
                sh """
                kubectl apply -f deployment-service.yml
                sleep 60
                """
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'Fastman', contextName: '', credentialsId: 'kubenetes', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://3462B304710E427F469369365B220D6A.gr7.us-east-1.eks.amazonaws.com') { 
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
