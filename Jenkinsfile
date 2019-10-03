pipeline {
    agent {
        kubernetes {
            label 'robot-shop'
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
         stage('Validating Docker') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    echo '--- Docker Version ---'                    
                    sh 'docker --version && systemctl daemon-reload && systemctl enable docker --now'
                }
            }
        }
        stage('Pulling Kubernetes') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    sh ' docker pull bitnami/kubectl:latest'
                }
            }
        }
    }
}