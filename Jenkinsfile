pipeline {
    agent any
    
    stages {
       
        stage("build") {
              when{
               expression {
                env.BRANCH_NAME =='s.hareere500-dev-patch-50009' 

               }
            }
            steps {
                
                echo 'building the application'
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
            }
        }
        stage("deploy") {
              when{
               expression {
                env.BRANCH_NAME  =='dev'

               }
            }
            steps {
                
                echo 'deploying the application'
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
