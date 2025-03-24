@Library('Shared') _

pipeline{
    agent { label 'jenkins-slave'}

    stages{
        stage("Code clone"){
            steps{
                echo "Clonning"
                sh "whoami"
                script{
                    clone("https://github.com/deepeshbarod80/Django-CICD.git","main")
                }
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
                    docker_push("notes-app", "latest", "DockerHubUser")
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
        stage("Cleanup"){
            steps{
                script{
                   docker_cleanup.removeAllUnusedResources()
                }
            }
        }
    }
}
