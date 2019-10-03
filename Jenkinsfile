pipeline {
    agent {
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
         stage('Testing Containers') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    sh 'docker --version'
                }
                container('kubectl') {
                    sh 'kubectl version'
                }
            }
        }
        stage('Build Docker Image') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    //docker build
                    echo 'docker hace algo aquí'                    
                }
            }
        }
        stage('kubernetes') {
            container('kubectl') {
                sh 'kubectl get namespaces'
            }
        }
    }
}