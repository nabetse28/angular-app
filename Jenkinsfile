pipeline {

    agent {
        label 'windows-worker'
    }
    environment {
        BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
    }
    stages {

        stage('Delete Folders & Check Version') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {                
                powershell "echo 'Deleting folders & Checking [npm,ng] version...'"
                echo 'Name of Branch: ' + env.BRANCH_NAME
                powershell "ls C:/inetpub/wwwroot/esteban/dev/; cd C:/inetpub/wwwroot/esteban/dev/; rm -r *.*"
                powershell "ls C:/inetpub/wwwroot/esteban/dev/"
                powershell "cd C:/inetpub/wwwroot/esteban/dev/; ls"
                powershell "ls"
                powershell "npm --version; ng --version"
            }
        }

        stage('Install Dependencies & Test') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                powershell "echo 'Installing npm dependencies...'"
                powershell "ls"
                powershell "npm install"
                powershell "ng lint; ng test"
            }
        }

        stage('Build') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                powershell "echo 'Building application...'"
                powershell "ng build --prod"
                powershell "ls"
                
            }
        }

        stage('Deploy') {
            when {branch pattern: "(dev|prod)", comparator: "REGEXP"}
            steps {
                powershell "echo 'Deploying application...'"
                powershell "cp -r ./dist/clase6/*.* C:/inetpub/wwwroot/esteban/dev/"
                powershell "cd C:/inetpub/wwwroot/esteban/dev/; ls"
            }
        }
  }

}