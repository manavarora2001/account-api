pipeline {

    agent any
    environment {
        NEW_VERSION = '1.5.0'
    }
    tools {
        maven 'Maven'
    }
    parameters {
        string (name : 'VERSION', defaultVaue : '' , description : 'version to deploy on prod')
        booleanParam(name: 'executeTests', defaultValue: true , description: '')
    }
    
    stages {
    
       stage ("build") {
          when {
              expression {
                  BRANCH_NAME == 'master' || BRANCH_NAME == 'dev'
                  echo "building version ${NEW_VERSION}"
                  sh "mvn clean install"
              }
          }
         steps {
             echo 'building the application ....'
         }         
       }
       
      stage ("test") {
          when {
              expression {
                  (BRANCH_NAME == 'master' || BRANCH_NAME == 'dev') && params.executeTests
              }
          }
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
            echo 'in always section ....'
        }
        success {
            //execute this if build is success     
            echo 'Build is SUCCESS section ....'
        }
       failure {
            //execute this if build is success
            echo 'Build is FAILURE section ....'
        }

        
    }
 }
