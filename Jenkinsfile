pipeline {
  agent any
  stages {

      stage('MVN compile') {
       steps {
        sh "mvn compile"      
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
         steps {   nexusArtifactUploader artifacts: [[artifactId: 'tp-foyer', classifier: '', file: '/var/lib/jenkins/workspace/TP-FOYER/target/tp-foyer-5.0.0.jar', type: 'jar']], credentialsId: 'Nexus', groupId: 'org.springframework.boot', nexusUrl: '192.168.252.129:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://192.168.252.129:8081/repository/maven-releases/', version: '3.3.4'    
         }
        }
}
}
