pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('af646b69-e51b-4b90-af42-6d6c36103263') 
    }
    tools{
        maven 'Maven'
    }
    
    stages {
       
        stage("build") {
             
            steps {
                
                echo "building the application ${NEW_VERSION}"
                  echo 'building the application ${NEW_VERSION}'
           }
        }
        stage("test") {
          when{
               expression {
                env.BRANCH_NAME =='s.hareere500-dev-patch-50009' || env.BRANCH_NAME =='dev'

               }
            }
            steps {
                
                echo 'testing the application'
                sh 'mvn install'
            }
        }
        stage("deploy") {
             
            
            steps {
                
                echo "deploying the application with ${SERVER_CREDENTIALS}"
                withCredentials([
                         usernamePassword(
                        credentials:'af646b69-e51b-4b90-af42-6d6c36103263',
                        usernameVariable:USER,     
                        passwordVariable:PWD) 
                    ]) { 

                        echo "some script ${USER} and ${PWD}"   

                } 
            }
        }
    }
    post {
        always{
            echo ' the building is done'

        }
        success{
            echo 'success'

        }
        failure{
            echo 'failure'

        }
        
    }
}
