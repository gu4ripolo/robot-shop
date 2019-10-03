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
                    sh 'docker --version'
                }
            }
        }
        stage('Pulling Kubernetes') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    sh 'docker pull lachlanevenson/k8s-kubectl'
                }
            }
        }
    }
}