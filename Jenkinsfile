pipeline {

    agent {
        label 'windows-worker'
    }
    stages {

        stage('Delete Folders & Check Version') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                bat "dir C:\inetpub\wwwroot\esteban\dev"
                bat "npm --version & ng --version"
            }
        }

        stage('Install Dependencies & Test') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                bat "echo 'Installing npm dependencies...'"
                bat "dir"
                bat "npm install"
                bat "ng lint & ng test"
            }
        }

        stage('Build') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                bat "ng build --prod"
            }
        }

        stage('Deploy') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                bat "echo 'Deploy"
            }
        }
  }

}