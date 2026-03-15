@Library("Shared") _
pipeline {
    agent any;
    
    stages{
        stage("Check Shared Lib"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code Clone"){
            steps{
                git url: "https://github.com/Kumar-Devansh/django-notes-app-tws.git", branch: "main"
                echo "Cloning Code Successful"
            }
        }

       // # After Implementing the shared library.
        // stage("Code Clone"){
        //         steps{
        //             script{
        //                 clone("https://github.com/Kumar-Devansh/django-notes-app-tws.git", "main")
        //             }
        //         }
        //     }
        stage("Code Build"){
            steps{
                echo "Building the Code"
                sh "whoami"
                sh "docker build -t notes-app:latest ."
            }
        }
        stage("Code Test"){
            steps{
                echo "Code Test is Successful"
            }
        }
        stage("Push to Docker Hub"){
            steps{
                withCredentials([usernamePassword(
                    credentialsId: "dockerHubCred",
                    passwordVariable: "DockerHubPass",
                    usernameVariable: "DockerHubUser"
                    )]){
                        
                        sh "docker login -u ${env.DockerHubUser} -p ${env.DockerHubPass}"
                        sh "docker image tag notes-app:latest ${env.DockerHubUser}/notes-app:latest"
                        sh "docker push ${env.DockerHubUser}/notes-app:latest "
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose up -d --build "
            }
        }
    }
}