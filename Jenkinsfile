@Library("Shared") _
pipeline {
    agent { label "vinod" }

    stages {
        stage("hello") {
            steps {
                script {
                    hey()
                }
            }
        }
        
        stage("Pull") {
            steps {
                script {
                    clone("https://github.com/Tushar-Shillarkar/LondheShubham153-django-notes-app.git", "main")
                }
            }
        }
        
        stage("Build") {
            steps {
                script {
                    
                    dockerBuild("notes-app", "latest", "tusharshillarkar")
                }
            }
        }
        
        stage("Test") {
            steps {
                echo "test the code"
            }
        }
        
        stage("Push") {
            steps {
                script {
                    DockerPush("notes-app", "latest", "tusharshillarkar")
                }
            }
        }
        
        stage("Deploy") {
            steps {
                echo "deploy the code"
                sh "docker compose up -d"
                sh "docker image tag notes-app:latest tusharshillarkar/notes-app:latest"
                sh "docker push tusharshillarkar/notes-app:latest"
            }
        }
    }
}
