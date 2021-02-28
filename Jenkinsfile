 def gv
pipeline {
    agent any
    parameters{
        choice(name: 'VERSION',choices:['1.1','1.2','2.0','2.2'],description:'version')
        booleanParam(name: 'executedTests', defaultValue: true , description: 'executedTests')
    }
    
    stages {
       
        stage("init") {
             
            steps {
                
               script{

                   gv =load "script.groovy"
               }
           }
        }
        stage("build") {
             
            steps {
                
               script{

                   gv.buildApp()
               }
           }
        }
        stage("test") {
          when{
               expression {
                 params.executedTests
               }
            }
            steps {
                
                 script{

                   gv.testApp()
               }
            }
        }
        stage("deploy") {
             
            
            steps {
                
                script{

                   gv.deployApp()
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
