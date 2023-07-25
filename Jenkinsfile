pipeline {
    
    agent {
        docker {
            //label 'docker'
            image 'python:latest'
            args '-u root' // This allows running commands as root in the container
        }
    }

    beforeAgent {
        // Install Docker inside the Jenkins agent container
        sh 'apt-get update'
        sh 'apt-get install -y docker.io'
        //sh 'apt-get install -y python3'
        sh 'usermod -aG docker jenkins'
    }

    stages {
        stage('Compile') {
            steps {
                sh 'python3 -m compileall adder.py'
            }
        }

        stage('Run') {
            steps {
                sh 'python3 adder.py 3 5'
            }
        }

        stage('Unit test') {
            steps {
                sh 'python3 -m unittest adder.py'
            }
        }
    }
}


// pipeline {
//     agent any
//     stages{
//         stage('Example'){
//             steps{
//                 echo 'Hello World'
//             }
//         }
//     }
// }


// node {
//     // This will run on a node with Docker installed
//     docker.image('python:latest').inside {
//         stage('Compile') {
//             sh 'python3 -m compileall adder.py'
//         }

//         stage('Run') {
//             sh 'python3 adder.py 3 5'
//         }

//         stage('Unit test') {
//             sh 'python3 -m unittest adder.py'
//         }
//     }
// }

