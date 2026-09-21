@Library("shared") _
pipeline{
    agent { label "Agent-ramesh"}
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
           steps{
               script{
                   clone("https://github.com/devopsramesh1995/django-notes-app1.git","main")
               }
           } 
        }
        stage("build"){
            steps{
                script{
                    docker_build("notes-app","latest","ramesh16082022")
                }
            } 
        }
        stage("test"){
            steps{
                echo "this is testing the code"
            } 
        }
        stage("push"){
            steps{
                script{
                    docker_push("notes-app","latest","ramesh16082022")
                }
            }
        }
        stage("deploy"){
            steps{
                echo "this is deploying the code"
                sh "docker compose down && docker compose up -d"
            } 
        }
    }
    
}
