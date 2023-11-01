pipeline {
    agent any

    environment {
        // Define any environment variables here
        JAVA_HOME = env.JAVA_HOME
        MVN_HOME = env.MVN_HOME
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/PallaviVangari/chatroomapplication.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Navigate to the project directory
                    dir('chatroomapplication') {
                        // Build the project
                        sh '${MVN_HOME}/bin/mvn clean install'
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Navigate to the project directory
                    dir('chatroomapplication') {
                        // Run tests
                        sh '${MVN_HOME}/bin/mvn test'
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deploy commands here
            }
        }
    }

    post {
        success {
            echo 'Build, test, and deploy were successful!'
        }
        failure {
            echo 'Build, test, or deploy failed!'
        }
    }
}
