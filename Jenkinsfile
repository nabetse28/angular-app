pipeline {

    agent {
        label 'windows-worker'
    }
    stages {

        stage('Check Version') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                bat "npm --version"
            }
        }

        stage('Install Dependencies') {
            steps {
                bat "echo 'Installing npm dependencies...'"
                bat "ls"
                bat "npm install"
            }
        }

        stage('Build') {
            steps {
                bat "echo 'Build'"
            }
        }

        stage('Deploy') {
            steps {
                bat "echo 'Deploy"
            }
        }
  }

}