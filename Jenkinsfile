pipeline {
    agent {
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
        stage('Build Docker Image') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('docker') {
                    //docker build
                    sh 'docker --version'                  
                }
            }
        }
    }
}