@Library("Shared) _
pipeline {
    agent { label "dev" }

    stages {
        stage("Clone") {
            steps {
                scripts{
                     hello()
                }
                echo "clone the project"
                git url:"https://github.com/DheerenGaud/Jenkins-learning.git",
                branch : "declarative_pipeline"
            }
        }
        stage("Build") {
            steps {
                echo "Code Build Stage"
                  sh "docker build -t node_jenkins_app ."
            }

        }
      stage("Push to DockerHub") {
         steps {
            echo "Pushing to Docker Hub"
            withCredentials([usernamePassword(credentialsId: 'dockerCredentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
            sh """
                echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                docker image tag node_jenkins_app dheerengaud/node_jenkins_app:latest
                docker push dheerengaud/node_jenkins_app:latest
            """
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
