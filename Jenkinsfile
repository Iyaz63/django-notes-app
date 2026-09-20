@Library("shared") _
pipeline{
    agent {label "Agent1"}
    
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
                    clone("https://github.com/Iyaz63/django-notes-app.git","main")
                 }
             }
         }
         stage("Build"){
             steps{
                 script{
                     docker_build("notes-app","latest","mohammediyaz")
                 }
                 
             }
         }
         stage("Puch to DockerHub"){
             steps{
                 script{
                     docker_push("notes-app","latest","mohammediyaz")
                 }
             }
         }
         stage("Deploy"){
             steps{
                 echo "This is Deploying the code"
                 sh "docker compose up -d --build"
             }
         }
    }
}
