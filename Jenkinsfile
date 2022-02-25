pipeline {

    agent {
        label 'windows-worker'
    }
    environment {
        BRANCH_NAME = "${GIT_BRANCH}"
    }
    stages {

        stage('Delete Folders & Check Version') {
            
            steps {
                script {
                    powershell "echo 'Deleting folders & Checking [npm,ng] version...'"
                    if (env.BRANCH_NAME == 'dev') {
                        powershell "echo 'Deleteting files for ${BRANCH_NAME}...'"
                        powershell "ls C:/inetpub/wwwroot/esteban/dev/; cd C:/inetpub/wwwroot/esteban/dev/; rm -r -force *"
                        powershell "ls C:/inetpub/wwwroot/esteban/dev/"
                    } else if (env.BRANCH_NAME == 'prod'){
                        powershell "echo 'Deleteting files for ${BRANCH_NAME}...'"
                        powershell "ls C:/inetpub/wwwroot/esteban/prod/; cd C:/inetpub/wwwroot/esteban/prod/; rm -r -force *"
                        powershell "ls C:/inetpub/wwwroot/esteban/prod/"
                    }
                    powershell "echo 'Checking version of angular and node...'"
                    powershell "npm --version; ng --version"
                }            
                
                
               
            }
        }

        stage('Install Dependencies') {
            when {branch pattern: "(dev|prod|PR-.*)", comparator: "REGEXP"}
            steps {
                powershell "echo 'Installing npm dependencies...'"
                powershell "npm install"
            }
        }
        stage('Test') {
            when {branch pattern: "(dev|PR-.*)", comparator: "REGEXP"}
            steps {
                powershell "echo 'Running tests...'"
                powershell "ng lint; ng test"
            }
        }

        stage('Build') {
            when {branch pattern: "(dev|prod|PR-.*)", comparator: "REGEXP"}
            steps {
                script{

                    powershell "echo 'Building application...'"

                    if (env.BRANCH_NAME == 'dev' || env.BRANCH_NAME == 'prod')
                    powershell "ng build --prod"
                    powershell "ls"
                }
                
            }
        }

        stage('Deploy') {
            steps {
                // when {branch pattern: "(dev|prod|PR-.*)", comparator: "REGEXP"}
                script {
                    powershell "echo 'Deploying application...'"
                    if (env.BRANCH_NAME == 'dev') {
                        powershell "cp -r ./dist/clase6/*.* C:/inetpub/wwwroot/esteban/dev/"
                        powershell "cd C:/inetpub/wwwroot/esteban/dev/; ls"
                    } else if (env.BRANCH_NAME == 'prod'){
                        powershell "cp -r ./dist/clase6/*.* C:/inetpub/wwwroot/esteban/prod/"
                        powershell "cd C:/inetpub/wwwroot/esteban/prod/; ls"
                    }
                }
                
                
            }
        }
  }

}