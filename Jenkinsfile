pipeline {
    agent any
    parameters{
        choice(name: 'VERSION_NUMBER',choices:['1.1','1.2','2.0','2.2'],description:'version')
        booleanParam(name: 'executedTests', defaultValue: true , description: 'executedTests')
    }
    
    stages {
       
        stage("build") {
             
            steps {
                
                echo "building the application"
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
