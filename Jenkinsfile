pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
              withKubeConfig(caCertificate: '', clusterName: 'aks-micro', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: ' aks-micro-dns-1tc39uzk.hcp.eastus.azmk8s.io') {
               sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                 withKubeConfig(caCertificate: '', clusterName: 'aks-micro', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: ' aks-micro-dns-1tc39uzk.hcp.eastus.azmk8s.io') {
               sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
