@Library("belajar-jenkins-shared-library@main") _

import latihangroovy.jenkins.Output;

// pipeline {
//     agent any
//     stages {
//         stage("Hello World") {
//             steps {
//                 script {
//                     hello.world()
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent any
    stages {
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
