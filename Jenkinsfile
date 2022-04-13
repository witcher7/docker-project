pipeline {
    agent any

    environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

    stages {


        stage('gitclone') {

			steps {
				git 'https://gitlab.com/madhosh01yagnik/techworld-js-docker-demo-app.git'
			}
		}


        stage('Build') {

			steps {
				sh 'docker build -t yagnikm/nodeapp_test:latest .'
			}
		}

        stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}


        stage('Push') {

			steps {
				sh 'docker push yagnikm/nodeapp_test:latest'
			}
		}
	}

	post {
		    always {
			sh 'docker logout'
		    }
	    }
        
}













}
