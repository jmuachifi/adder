pipeline {
    
    agent none // No default agent, will be specified later

    stages {
        stage('Install Docker') {
            agent {
                // Use a basic agent for Docker installation
                docker {
                    image 'python:latest'
                    args '-u root' // This allows running commands as root in the container
                }
            }
            steps {
                // Install Docker inside the Jenkins agent container
                sh 'apt-get update'
                sh 'apt-get install -y docker.io'
                sh 'usermod -aG docker jenkins'
            }
        }

        stage('Compile, Run, and Unit test') {
            agent {
                docker {
                    // Specify Python image as the agent after Docker is installed
                    image 'python:latest'
                }
            }
            steps {
                // Your previous stages' steps go here
                sh 'python3 -m compileall adder.py'
                sh 'python3 adder.py 3 5'
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

