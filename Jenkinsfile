pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8sp-token', namespace: 'webapps', serverUrl: 'https://3C9531FC57993A440EB7AA364FBFA63C.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham1', contextName: '', credentialsId: 'k8sp-token', namespace: 'webapps', serverUrl: 'https://3C9531FC57993A440EB7AA364FBFA63C.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
