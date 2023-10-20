pipeline{

 agent any
   tools{
    maven 'Maven_Home'
        } 
  stages{
    stage('Build'){
     steps{
      sh 'mvn clean package'
     }
    post{
      success{
        echo "Archiving the Artifacts"
        archiveArtifacts artifacts: '**/target/*.war'
        }   
      }
   }
  
 stage('deploy to tomcat server'){
  steps{
   deploy adapters: [tomcat9(credentialsId: '8aa04c82-06ef-448b-9dc4-20c8a41aba7f', path: '', url: 'http://184.72.169.143:8080/')], contextPath: null, war: '**/*.war'
     }
   }
 }
}
