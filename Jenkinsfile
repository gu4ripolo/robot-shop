pipeline {
    agent {
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'KubernetesPods.yaml'
        }
    }
    stages {
         stage('test') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                echo 'test'
                container('maven') {
                    sh 'mvn -version'
                }
            }
        }
    }
}