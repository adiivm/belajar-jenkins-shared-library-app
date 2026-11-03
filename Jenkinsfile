pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }
    
    stages {
        stage('Hello') {
            steps {
                echo ("Hello World Adi")
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