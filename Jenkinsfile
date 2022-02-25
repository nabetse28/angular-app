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

        stage('Install Dependencies & Test') {
            steps {
                bat "echo 'Installing npm dependencies...'"
                bat "dir"
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