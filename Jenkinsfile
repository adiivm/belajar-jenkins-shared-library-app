pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }
    
    stages {
        stage('Build') {
            steps {
                echo ("Start Build")
                sh("./mvnw clean compile test-compile")
                echo ("Finish Build")
            }
        }
        stage('Test') {
            steps {
                echo ("Start Test")
                sh("./mvnw test")
                echo ("Finish Test")
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