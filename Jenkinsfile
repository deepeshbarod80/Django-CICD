@Library('Shared')_

pipeline{
    agent { label 'jenkins-slave'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
            clone("https://github.com/deepeshbarod80/Django-CICD.git","main")
            }
        }
        stage("Code Build"){
            steps{
            docker_build("notes-app","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                docker_push("notes-app", "latest", "dockerHubCreds")
            }
        }
        stage("Deploy"){
            steps{
                deploy_compose()
            }
        }
        
    }
}
