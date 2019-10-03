pipeline {
    agent {
        kubernetes {
            label 'master'
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
                }
            }
        }
    }
}