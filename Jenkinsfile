pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
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
