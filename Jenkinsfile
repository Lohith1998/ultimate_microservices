pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: ' LOHITH-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://E038A102B0BCE364891C26647E177E81.gr7.us-east-1.eks.amazonaws.com') {
    // some block
}
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: ' LOHITH-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://E038A102B0BCE364891C26647E177E81.gr7.us-east-1.eks.amazonaws.com') {
    // some block
}
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
