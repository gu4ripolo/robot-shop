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
                    sh 'apt-get update && apt install docker.io && systemctl start docker && systemctl enable docker'
                    sh 'docker --version'
                }
            }
        }
    }
}