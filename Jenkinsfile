pipeline { 
 
   agent any 
   tools {
    maven 'Apache Maven 3.6.2'
  }
   
    stages {
       
       stage('Checkout'){
          steps{
             sh 'ls'
          def url = sh(returnStdout: true, script: 'git config.remote.origin.url').trim()
        print url
          }
       }
    }
}
