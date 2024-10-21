pipeline {
  agent any
  stages {
     stage('MVN version') {
      steps {
        sh "mvn -version"      
      }
    }
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
  }
}
