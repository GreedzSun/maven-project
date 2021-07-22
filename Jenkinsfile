pipeline {
  agent any
  triggers{
    pollSCM('*/5 * * * *')
  }
  tools {maven "localMaven"
  }
  stages{
      stage ('Build'){
        steps {
          sh 'mvn clean package'
          }        
        post {
          success{
          echo "Archiving.."
          archiveArtifacts artifacts:'**/target/*.war'
        }
       }
      }
       stage ('Deployments'){
         parallel{
           stage ('Deplot to Staging'){
            steps {
            	sh "cp **/target/*.war /home/bi/apache-tomcat-9.0.50/webapps"
            }        
           }
           stage ('Deploy to prod'){
            steps {
            timeout (time:5, unit:'DAYS'){
            input message:'Approve Prod deployment?'
           }
           		sh "cp **/target/*.war /home/bi/tomcat-prod/webapps"
          }
       }
    }
}
}
}
