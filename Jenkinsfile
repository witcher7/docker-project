pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('af646b69-e51b-4b90-af42-6d6c36103263') 
    }
    tools{
        maven 'Maven'
    }
    parameters{
        string(name: 'VERSION' , defaultValue:' ', description: 'version to deploy on prod')
        choice(name: 'VERSION_NUMBER',choices:['1.1','1.2','2.0','2.2'],description:'version')
        booleanParam(name: 'executedTests', defaultValue: true , description: 'executedTests')

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
                env.BRANCH_NAME =='s.hareere500-dev-patch-50009'  && executedTests
               }
            }
            steps {
                
                echo 'testing the application'
            }
        }
        stage("deploy") {
             
            
            steps {
                
                echo "deploying the application with version number:${params.VERSION_NUMBER}"
               
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
