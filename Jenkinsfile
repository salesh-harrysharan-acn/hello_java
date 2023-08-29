pipeline {
    agent any 

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'mvn clean install' // or any other build command
                    } else {
                        bat 'mvn clean install' // or any other build command
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        echo './run-tests.sh'
                    } else {
                        echo 'run-tests.bat'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Build and Test stages completed successfully.'
        }

        failure {
            echo 'One of the stages failed.'
        }
    }
}
