pipeline {

    agent {
        label 'windows-worker'
    }
    stages {

        stage('Check Version') {
            when {branch 'dev|prod'}
            steps {
                bat "npm --version"
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