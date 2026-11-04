pipeline {
    agent none
    
    stages {
        stage('Build') {
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                script {
                    for (int i = 0; i< 10; i++) {
                        echo("Script ${i}")
                    }
                }
                echo ("Start Build")
                sh("./mvnw clean compile test-compile")
                echo ("Finish Build")
            }
        }
        stage('Test') {
            steps {
                
                script {
                    def data = [
                        "firstname": "Adi",
                        "lastname" : "Kurniadi"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
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