@Library("shared") _
pipeline{
    agent {
      docker {
        image 'abhishekf5/maven-abhishek-docker-agent:v1'
        args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
       }
     }
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
