pipeline {
    agent {
        kubernetes {
            label 'master'
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
        stage('Pulling Kubernetes') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                echo 'test'
            }
        }
    }
}