pipeline {
    agent any
    stages {
        stage("run frontend") {
            steps {
                echo "i am installing yarn from nodejs"
                nodejs('nodejs-10.17.0') {
                    bat 'yarn install'
                }
            }
        }
        stage("run backend") {
            steps {
                bat 'executing gradle'
                withGradle() {
                    bat './gradlew -v'
                }
            }
        }
    }
}
