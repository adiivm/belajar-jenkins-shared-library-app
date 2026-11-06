@Library("belajar-jenkins-shared-library@main") _

import latihangroovy.jenkins.Output;

pipeline {
    agent any
    stages {
        stage("Maven Compile") {
            steps {
                script {
                    maven("clean compile")
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
