@Library("Shared") _
pipeline {
    agent { label "dev" }

    stages {
        stage("Clone") {
            steps {
                script{
                clone("https://github.com/DheerenGaud/Jenkins-learning.git","declarative_pipeline")
                }
            }
        }
        stage("Build") {
            steps {
                echo "Code Build Stage"
                script{
                 docker_build("node_jenkins_app","latest")
                }
            }

        }
      stage("Push to DockerHub") {
          steps {
             echo "Pushing to Docker Hub"
             script{
             dockerPush("node_jenkins_app", "dheerengaud/node_jenkins_app","dockerCredentials")
             }
            }
       }
      stage("Deploy") {
            steps {
                sh "docker compose up -d"
                echo "Deployed done"
            }
        }
    }
}
