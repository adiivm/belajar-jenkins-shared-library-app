pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }
    
    stages {
        stage('Build') {
            steps {
                echo ("We are Build something here")
            }
        }
        stage('Test') {
            steps {
                echo ("We are Testing something here")
            }
        }
        stage('Deploy') {
            steps {
                echo ("We are Deploying something here")
            }
        }
    }

    post {
        always {
            echo "I will always say Hello to you brother by default"
        }

        success {
            echo "Yay, Your succesfull bro"
        }

        failure {
            echo "oh no, you get failure"
        }

        cleanup {
            echo "Don't care success or error"
        }
    }
} 