def gv 
pipeline {

    agent any

    parameters{
        string(name: 'VERSION' , defaultValue :'', description : 'version to deploy on prod')
        choice(name: 'VERSION' , choices: ['1.1.0' , '1.2.0' ,'1.3.0'],  description : '')
        booleanParam(name: 'executeTests' , defaultValue :true, description : '')

    }

    environment {
        NEW_VERSION = "1.3.0"
        SERVER_CREDENTIALS = credentials("server-credentials")
    }

    stages {

        satge("init) {

            steps{

                script{
                    gv = load "script.groovy"
                }

            }

        }

        stage("build") {

            steps{
                script{
                    gv.buildApp()
                }
            }
        }

        stage("test") {

            when {
                expression{
                    params.executeTests
                }
            }

            steps{
                script{
                    gv.testApp()
                }
            }
        }

        stage("deploy") {

            steps{
                script{
                    gv.deployApp()
                }                 
            }
        }
    }
}
