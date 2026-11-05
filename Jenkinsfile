pipeline {
    agent none

    environment {
        AUTHOR = "Adi Kurniadi"
        EMAIL = "adi.kurniadi@gmail.com"
        WEB = "https://dekurtz.blogspot.com"
    }

    triggers {
        cron("*/5 * * * *")
        pollSCM("*/5 * * * *")
        upstream(upstreamProjects: 'job1,job2', threshold:hudson.model.Result.SUCCESS)
    }

    parameters {
        string(name: "NAME", defaultValue: "Guest", description: "What is your name?")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "Tell me about you")
        booleanParam(name: "DEPLOY_TO_PROD", defaultValue: false, description: "Need to Deploy?")
        choice(name: "SOCIAL_MEDIA", choices: ['IG', 'FB', 'TWIT'], description: "Which Social Media?")
        password(name: "SECRET", defaultValue: "", description: "Encrypt Key")
    }

    options {
        disableConcurrentBuilds(abortPrevious: false) 
        timeout(time: 10, unit: 'MINUTES')
    }
    
    stages {
        stage("Parameter") {
            environment {
                APP = credentials("adi_kurniadi")
            }
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                echo "Hello ${params.NAME}"
                echo "You description is ${params.DESCRIPTION}"
                echo "Your social media is ${params.SOCIAL_MEDIA}"
                echo "Need to deploy : ${params.DEPLOY} to deploy!"
                echo "Your secret is ${params.SECRET}"
            }
        }
        stage("Prepare") {
            environment {
                APP = credentials("adi_kurniadi")
            }
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
                echo("App User : ${APP_USR}")
                sh('echo "App Password : $APP_PSW" > "password.txt"')
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
            input {
                message "can we deploy?"
                ok "Yes, of course"
                submitter "pzn,adi"
                parameters {
                    choice(name: "TARGET_ENV", choices: ['DEV','QA', 'PROD'], description: "Which Environment?")
                }
            }
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                echo ("Deploy to ${TARGET_ENV}")

            }
        }

        stage('Release') {
            when {
                expression {
                    return params.DEPLOY
                }
            }
            agent {
                node{
                    label "linux && java11"
                }
            }
            steps {
                echo("Release it")
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