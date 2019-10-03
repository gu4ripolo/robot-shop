pipeline {
    agent {
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
         stage('Pulling kubernetes image') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    echo '--- Docker Version ---'                    
                    sh 'docker --version'
                    echo '--- Pulling Kubernetes ---' 
                    sh 'docker pull bitnami/kubectl'
                    echo '--- Validating Kubernetes ---' 
                    sh 'kubectl get pods'
                }
            }
        }
    }
}