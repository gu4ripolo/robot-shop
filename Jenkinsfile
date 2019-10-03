pipeline {
    agent {
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
         stage('Docker Version') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                echo 'test'
                container('docker') {
                    sh 'docker --version'
                }
            }
        }
    }
}