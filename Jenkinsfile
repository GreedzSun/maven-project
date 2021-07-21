pipeline {
  agent any
  stages{
      stage ('Build'){
        steps {
          sh 'mvn clean package'
          echo "Maven build step..."
        }        
        post {
          success{
          echo "Archiving.."
          archiveArtifacts artifacts:'**/traget/*.war'
        }
       }
       stage ('Build'){
        steps {
          echo "Build step"
        }        
       }
      stage ('Deploy'){
        steps {
          echo "Deploy step"
        }        
       }
      stage ('End'){
        steps {
          echo "End step"
        }        
       }
    }
}
