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
                        sh 'make' // or any other build command
                    } else {
                        bat 'build.bat' // or any other build command
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh './run-tests.sh'
                    } else {
                        bat 'run-tests.bat'
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
