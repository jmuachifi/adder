pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.image('python:latest').inside {
                        sh 'python3 -m compileall adder.py'
                    }
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    docker.image('python:latest').inside {
                        sh 'python3 adder.py 3 5'
                    }
                }
            }
        }

        stage('Unit test') {
            steps {
                script {
                    docker.image('python:latest').inside {
                        sh 'python3 -m unittest adder.py'
                    }
                }
            }
        }
    }
}


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

