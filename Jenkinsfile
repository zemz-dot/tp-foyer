pipeline {
  agent any
  stages {
    stage('Dev') {
      steps {
        echo 'Hello'
      }
    }
     stage('Testing Maven') {
      steps {
        sh "mvn -version"      
      }
    }
  }
}
