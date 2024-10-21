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
stage('Sonarqube Analysis - SAST') {
steps {
withSonarQubeEnv('SonarQube') {
sh "mvn sonar: sonar \
-Dsonar.projectKey-maven-jenkins-pipeline \
-Dsonar.host.url=http://192.168.252.129:9000"
}
}
}
}
}
