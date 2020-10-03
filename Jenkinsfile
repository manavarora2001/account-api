pipeline {

    agent any
    environment {
        NEW_VERSION = '1.5.0'
    }
    tools {
        maven 'Maven'
    }
    parameters {
        choice(name: 'VERSION', choices :['1.1.0','1.2.0','1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true , description: '')
    }
    
    stages {
    
       stage ("build") {
          when {
              expression {
                  BRANCH_NAME == 'master' || BRANCH_NAME == 'dev'
                  echo "building version ${NEW_VERSION}"
                  sh "cd account-api"
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
