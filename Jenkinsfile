pipeline{
    agent any
    stages{
        stage('run node'){
            steps{
                echo 'running nodejs...'
                nodejs('Node-18.16){
                    sh 'npm install .env'
                }
            }
        }
    }
}
