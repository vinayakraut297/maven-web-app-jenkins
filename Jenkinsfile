@Library('my_shared_libraries') _

pipeline {
    agent any
tools{

    maven "Maven-3.9.4"
}
    stages {
        stage('clone') {
            steps {
              git branch: 'main', credentialsId: 'Git-Credential', url: 'https://github.com/vinayakraut297/maven-web-app-jenkins.git'
            }
        }
         stage('build') {
            steps {
             mavenBuild()
            }
        }
          stage('codeReview') {
            steps {
             sonarQube()
            }
        }
    }
}
    
  /* stage('Push Image'){
        withCredentials([string(credentialsId: 'DOCKER-CREDENTIALS', variable: 'DOCKER_CREDENTIALS')]) {
            sh 'docker login -u ashokit -p ${DOCKER_CREDENTIALS}'
        }
        sh 'docker push ashokit/mavenwebapp'
    }
    
    stage('Deploy App'){
        kubernetesDeploy(
            configs: 'maven-web-app-deploy.yml',
            kubeconfigId: 'Kube-Config'
        )
    }    
}
/*
