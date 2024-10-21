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
}
}
