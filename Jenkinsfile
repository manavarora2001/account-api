pipeline {

    agent any
    
    stages {
    
       stage ("build") {
         steps {
             echo 'building the application ....'
         }         
       }
       
      stage ("test") {
         steps {
            echo 'testing the application ....'
         }         
       }


       stage ("deploy") {
         steps {
            echo 'deploying the application ....'
         }         
       }
    }
    
    post {
        always {
            //executed always if the build fails or succeeds
        }
        success {
            //execute this if build is success     
        }
       failure {
            //execute this if build is success     
        }

        
    }
 }
