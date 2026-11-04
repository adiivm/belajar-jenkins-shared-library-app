pipeline {
    agent none

    environment {
        AUTHOR = "Adi Kurniadi"
        EMAIL = "adi.kurniadi@gmail.com"
        WEB = "hhtps://dekurtz.blogspot.com"
    }
    
    stages {
        stage("Prepare") {
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                echo("Author : ${AUTHOR}")
                echo("Email : ${EMAIL}")
                echo("Web : ${WEB}")
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Branch Name : ${env.BRANCH_NAME}")
            }
        }

        
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
            agent {
                node {
                    label "linux && java11"
                }
            }
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
            agent {
                node {
                    label "linux && java11"
                }
            }
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