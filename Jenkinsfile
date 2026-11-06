@Library("belajar-jenkins-shared-library@main") _

import latihangroovy.jenkins.Output;

pipeline {
    agent any
    stages {
        stage("Library Resource") {
            steps {
                script {
                    def config = libraryResource("config/build.json")
                    echo(config)
                }
            }
        }
        stage("Hello Person") {
            steps {
                script {
                    hello.person([
                        firstName: "Adi",
                        lastName: "Kurniadi"
                    ])
                }
            }
        }
        stage("Maven Compile") {
            steps {
                script {
                    // maven("clean compile")
                    maven(["clean", "compile", "test"])
                }
            }
        }
        stage("Global Variable"){
            steps {
                script {
                    echo(author())
                    echo(author.name())
                    echo(author.channel())
                }
            }
        }
        stage("Hello World") {
            steps {
                script {
                    hello.world()
                }
            }
        }
        stage("Hello Groovy") {
            steps {
                script {
                    // Instantiate the object and pass 'this' (the pipeline context)
                    def output = new Output(this)
                    
                    // Call the method
                    output.hello("Groovy")
                }
            }
        }
    }
}
