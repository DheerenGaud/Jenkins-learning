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
