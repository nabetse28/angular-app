pipeline {

    agent {
        label 'windows-worker'
    }
    environment {
     BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
    }
    stages {

        stage('Check Version') {
            
            steps {
                bat "npm --version"
                echo env.BRANCH_NAME
            }
        }

        stage('Test') {
            steps {
                bat "echo 'Test'"
            }
        }

        stage('Build') {
            steps {
                bat "echo'Build'"
            }
        }

        stage('Deploy') {
            steps {
                bat "echo 'Deploy"
            }
        }

  }

}