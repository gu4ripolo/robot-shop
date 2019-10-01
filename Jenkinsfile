void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/gu4ripolo/robot-shop"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}

pipeline {
    agent any
    environment {
        //AWS_ACCESS_KEY_ID = credentials('aws_access_key')
        //AWS_SECRET_ACCESS_KEY = credentials('aws_secret_key')
        DOCKER_IMAGE_NAME = "safcdou/train-schedule"
    }
    stages {     
        stage('test') {
            steps {
                setBuildStatus("Build complete", "SUCCESS");
            }
        }
        stage('Pull Request') {
            when { expression { env.BRANCH_NAME ==~ /feat.*/ } }
            steps {
                /*echo 'Running build automation'
                    kubernetesDeploy(
                    kubeconfigId: 'kubeconfig',
                    configs: 'K8s/descriptors/*.yaml', 
                    enableConfigSubstitution: true
                ) */
                echo 'A new commit in the features branch has been detected'
                input(message: "Do you want to create a Pull Request?", ok: "yes")
                //httpRequest authentication: 'github_access', contentType: 'APPLICATION_JSON_UTF8', httpMode: 'POST', requestBody: """{ "title": "Pull Request Created Automatically by Jenkins", "body": "From Jenkins job: ${env.BUILD_URL}", "head": "gu4ripolo:${env.BRANCH_NAME}", "base": "master"}""", url: "https://api.github.com/repos/gu4ripolo/robot-shop/pulls"
            }
        }
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                echo 'algo'
            }
        }
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                echo 'algo mas'
            }
        }
        stage('DeployToProduction') {
            when {
                branch 'master'
            }
            steps {
                input 'Deploy to Production?'
                milestone(1)
                kubernetesDeploy(
                    kubeconfigId: 'kubeconfig',
                    configs: 'K8s/descriptors/*.yaml', 
                    enableConfigSubstitution: true
                ) 
            }
        }
    }
}
