@Library('Shared') _

pipeline{
    agent { label 'jenkins-slave'}

    stages{
        stage("Code clone"){
            steps{
                script{
                    clone("https://github.com/deepeshbarod80/Django-CICD.git","main")
                }
                echo "Clonning"
                sh "whoami"
                echo "Clone Successful"
            }
        }
        stage("Code Build"){
            steps{
                script{
                    docker_build("notes-app","latest", "DockerHubUser")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "deepeshbarod90")
                }
            }
        }
        stage("Deploy"){
            steps{
                script{
                   docker_compose() 
                }
            }
        }
        
    }
}
