pipeline {
  agent any
  stages {

      stage('MVN compile') {
       steps {
        sh "mvn compile"      
      }
    }
    stage('MVN package') {
      steps {
        sh "mvn package"      
      }
    }
    stage('Check JAR') {
  steps {
    sh "ls -l target/"
  }
}
       stage('Sonarqube Analysis') {
         steps {
         withSonarQubeEnv('Sonarqube') {
         sh "mvn sonar:sonar \
         -Dsonar.projectKey=DEVOPS1 \
         -Dsonar.host.url=http://192.168.252.129:9000"
}
}
}
        stage('Nexsus') {
         steps {   nexusArtifactUploader artifacts: [[artifactId: 'tp-foyer', classifier: '', file: 'target/*.jar', type: 'jar']], credentialsId: 'Nexus', groupId: 'org.springframework.boot', nexusUrl: '192.168.252.129:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://192.168.252.129:8081/repository/maven-releases/', version: '3.3.4'    
         }
        }
}
}
