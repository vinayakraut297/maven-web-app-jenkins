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
    
