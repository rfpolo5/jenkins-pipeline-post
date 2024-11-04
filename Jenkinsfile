pipeline {
    agent any
   
    stages {
        stage('Create  directory for the WEB Application')
        {
            steps{
               
                //Fisrt, drop the directory if exists
                sh 'rm -rf /home/rafaelpolo/Documentos/Estudio/install/Jenkins/tomcat'
                //Create the directory
                sh 'mkdir /home/rafaelpolo/Documentos/Estudio/install/Jenkins/tomcat'
                
            }
        }
        stage('Drop the Apache Tomcat Docker container'){
            steps {
            echo 'droping the container...'
            sh 'docker rm -f tomcat1'
            }
        }
        stage('Create the Tomcat container') {
            steps {
            echo 'Creating the container...'
            sh 'docker run -dit --name tomcat1 -p 9090:8080  -v /home/rafaelpolo/Documentos/Estudio/install/Jenkins/tomcat:/usr/local/tomcat/webapps tomcat:9.0'
            }
        }
        stage('Copy the web application to the container directory') {
            steps {
                echo 'Creating the shopping folder in the container'
                sh 'mkdir /home/rafaelpolo/Documentos/Estudio/install/Jenkins/tomcat/shopping'
                echo 'Copying web application...'             
                sh 'cp -r shopping/* /home/rafaelpolo/Documentos/Estudio/install/Jenkins/tomcat/shopping'
            }
        }
    }

    post {
        always {

            echo "ejecuta"
        
        }
        success {
        // One or more steps need to be included within each condition's block.
        echo 'the deployment has worked'
       }
       failure {
        // One or more steps need to be included within each condition's block.
        echo 'An error has ocurred'
      }
      cleanup{
          echo 'the deployment ....'
      }
 }
}
