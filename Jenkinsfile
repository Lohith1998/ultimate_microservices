pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(
                    caCertificate: '', 
                    clusterName: 'LOHITH-EKS',  // Removed extra space before the cluster name
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    restrictKubeConfigAccess: false, 
                    serverUrl: 'https://E038A102B0BCE364891C26647E177E81.gr7.us-east-1.eks.amazonaws.com'
                ) {
                    // Apply the Kubernetes deployment
                    sh "kubectl apply -f deployment-service.yml"
                    // Sleep for 60 seconds to allow deployment to stabilize
                    sleep 60
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeConfig(
                    caCertificate: '', 
                    clusterName: 'LOHITH-EKS',  // Removed extra space before the cluster name
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    restrictKubeConfigAccess: false, 
                    serverUrl: 'https://E038A102B0BCE364891C26647E177E81.gr7.us-east-1.eks.amazonaws.com'
                ) {
                    // Get the list of services in the 'webapps' namespace to verify deployment
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
