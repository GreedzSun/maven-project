pipeline {
  agent any
  stages{
      stage ('Build'){
        steps {
          sh 'mvn clean'
          sh 'mvn package'
          echo "Maven build step..."
        }        
        post {
          success{
          echo "Archiving.."
          archiveArtifacts artifacts:'**/traget/*.war'
        }
       }
      }
       stage ('Buildo'){
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
