pipeline {
   
   agent any 
    stages {
       
       stage('Checkout'){
          steps{
             
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
      
    }
}
