@Library('Shared') _

pipeline{
    agent { label 'jenkins-slave'}
    
    stages{
        stage("Code clone"){
            steps{
                echo "Clonning"
                sh "whoami"
            clone("https://github.com/deepeshbarod80/Django-CICD.git","main")
                echo "Clone Successful"
            }
        }
        stage("Code Build"){
            steps{
                echo "Building"
            docker_build("notes-app","latest")
                echo "Build Successful"
            }
        }
        stage("Push to DockerHub"){
            steps{
                echo "Pushing"
                docker_push("notes-app", "latest", "dockerHubCreds")
                echo "Push Successful"
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying"
                deploy_compose()
                echo "Deploy Successful"
            }
        }
        
    }
}
