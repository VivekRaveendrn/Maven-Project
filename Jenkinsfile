pipeline {
   
 
   agent any 
   tools {
    maven 'Apache Maven 3.6.2'
  }
   
    stages {
       
       stage('Checkout'){
          steps{
             sh 'ls'
          sh 'rm -rf Maven-Project'
          sh 'git clone https://github.com/VivekRaveendrn/Maven-Project.git'
          }
       }
       
       
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
       
       stage('Sonarqube') {
   
 steps {
        script {
          // requires SonarQube Scanner 2.8+
          scannerHome = tool 'SonarQube'
        }
        withSonarQubeEnv('SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
       }
       
       
       
       stage('Publish to Nexus'){
          
           
         steps{
           nexusArtifactUploader artifacts: [[artifactId: 'maven-simple', classifier: '', 
		  file: 'target/maven-simple-0.2-SNAPSHOT.jar', type: 'jar']], credentialsId: '1c1314d5-5d5b-42c4-bdee-6a28ff34e037', 
		  groupId: 'com.github.jitpack', nexusUrl: '34.93.81.29:8081', nexusVersion: 'nexus2', 
		  protocol: 'http', repository: 'maven-snapshots', version: '0.2-SNAPSHOT'
          }
       }
       
     
      
    }
}
