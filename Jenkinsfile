@Library('Shared') _

pipeline{
    agent { label 'jenkins-slave'}

    stages{
        stage("Code clone"){
            steps{
                echo "Clonning"
                sh "whoami"
                script{
                    code_checkout("https://github.com/deepeshbarod80/Django-CICD.git","main")
                }
                echo "Cloned Successful"
            }
        }
        stage("Code Build"){
            steps{
                echo "Building Code"
                script{
                    docker_build("notes-app","latest", "dockerHubUser")
                }
                echo "Built code Successfully"
            }
        }
        stage("Push to DockerHub"){
            steps{
                echo "Pushing Code"
                script{
                    docker_push("notes-app", "latest", "dockerHubUser")
                }
                echo "Pushed Successfully"
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying Code"
                script{
                   docker_compose() 
                }
                echo "Deployed Successfully"
            }
        }
    }
}
