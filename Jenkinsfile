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
                    Output.hello("Groovy")
                }
            }
        }
    }
}