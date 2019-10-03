pipeline {
    agent {
        kubernetes {
            label 'robot-shop'
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
        stage('Pulling Kubernetes') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                container('ubuntu') {
                    sh ' sudo apt-get update && sudo apt install docker.io && sudo systemctl start docker && sudo systemctl enable docker'
                    sh 'docker --version'
                }
            }
        }
    }
}