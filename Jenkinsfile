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
                scripts {
                    if(env.BRANCH_NAME == 'dev' || env.BRANCH_NAME == 'prod') {
                        bat "npm --version"
                    }
                }
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