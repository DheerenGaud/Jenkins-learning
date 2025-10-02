pipeline {
    agent any
    stages {
        stage("Clone") {
            steps {
                echo "clone the project"
                git url:"https://github.com/DheerenGaud/Jenkins-learning.git",
                branch : "declarative_pipeline"
            }
        }
        stage("Build") {
            steps {
                echo "Code Build Stage"
                // dir("Jenkins-learning"){
                  sh "docker build -t node_jenkins_app ."
                // }
            }

        }
        stage("Test") {
            steps {
                echo "test started"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deployed done"
            }
        }
    }
}
