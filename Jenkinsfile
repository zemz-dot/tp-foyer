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
    
    stage('MVN package') {
      steps {
        sh "mvn package"      
      }
    }
       stage('Sonarqube Analysis') {
         steps {
         withSonarQubeEnv('Sonarqube1') {
         sh "mvn sonar:sonar \
         -Dsonar.projectKey=tpfoyer \
         -Dsonar.host.url=http://192.168.252.129:9000"
}
}
}
        stage('Nexus') {
         steps {   nexusArtifactUploader artifacts: [
           [artifactId: 'tp-foyer', 
            classifier: '', 
            file: 'target/tp-foyer-5.0.0.jar', 
            type: 'jar']], 
           credentialsId: 'Nexus', 
           groupId: 'org.springframework.boot', 
           nexusUrl: '192.168.252.129:8081', 
           nexusVersion: 'nexus3', 
           protocol: 'http', 
           repository: 'maven-releases', 
           version: '3.3.4'    
         }
        }
}
}
