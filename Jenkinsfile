@Library("Shared") _
pipeline{
    
    agent { label "vinod"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
               script{
                clone("https://github.com/akashjavali/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","akashjavali")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","akashjavali")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
        stage("Test"){
            steps{
                echo "Code changes from github"
            }
        }
    }
}
