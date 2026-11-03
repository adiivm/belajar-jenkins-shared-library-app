pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }
    
    stages {
        stage('Build') {
            steps {
                echo ("We are Build something here 1")
                sleep(10)
                echo ("We are Build something here 2")
                echo ("We are Build something here 3")
            }
        }
        stage('Test') {
            steps {
                echo ("We are Testing something here 1")
                sleep(10)
                echo ("We are Testing something here 2")
                echo ("We are Testing something here 3")
            }
        }
        stage('Deploy') {
            steps {
                echo ("We are Deploying something here 1")
                echo ("We are Deploying something here 2")
                sleep(10)
                echo ("We are Deploying something here 3")
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