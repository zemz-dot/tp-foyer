pipeline {
  agent any
  stages {
      stage('MVN clean') {
       steps {
        sh "mvn clean"      
      }
    }
      stage('MVN compile') {
       steps {
        sh "mvn compile"      
      }
    }
node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=DEVOPS -Dsonar.projectName='DEVOPS'"
    }
  }
}  }
}
