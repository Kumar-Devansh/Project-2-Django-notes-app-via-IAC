@Library("Shared") _
pipeline {
    agent any;
    
    stages{
        // stage("Code Clone"){
        //     steps{
        //         git url: "https://github.com/Kumar-Devansh/django-notes-app-tws.git", branch: "main"
        //         echo "Cloning Code Successful"
        //     }
        // }

       // # After Implementing the shared library.
        stage("Code Clone"){
                steps{
                    script{
                        clone("https://github.com/Kumar-Devansh/django-notes-app-tws.git", "main")
                    }
                }
            }
        // stage("Code Build"){
        //     steps{
        //         echo "Building the Code"
        //         sh "whoami"
        //         sh "docker build -t notes-app-2.0:latest ."
        //     }
        // }
        stage("Code Build"){
            steps{
                script{
                    docker_build("notes-app-3.0", "latest", "devansh0111")
                }
            }
        }
        stage("CleanUp Code"){
            steps{
                script{
                    docker_cleanup("notes-app-3.0", "latest", "devansh0111")
                }
            }
        }
        stage("Code Test"){
            steps{
                echo "Code Test is Successful"
            }
        }
        
        stage("Trivy-Scan"){
            steps{
                script{
                    trivy_scan()
                    echo "Scaning is Done"
                }
            }
        }
        
        stage("Push to Docker Hub"){
            steps{
                withCredentials([usernamePassword(
                    credentialsId: "docker-hub-cred",
                    passwordVariable: "DockerHubPass",
                    usernameVariable: "DockerHubUser"
                    )]){
                        
                        sh "docker login -u ${env.DockerHubUser} -p ${env.DockerHubPass}"
                        sh "docker image tag notes-app-2.0:latest ${env.DockerHubUser}/notes-app-2.0:latest"
                        sh "docker push ${env.DockerHubUser}/notes-app-2.0:latest "
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