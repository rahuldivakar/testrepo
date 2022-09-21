
 
pipeline {
    /* specify nodes for executing */
    agent any
 environment {
    FULL_PATH_BRANCH = "${sh(script:'git name-rev --name-only HEAD', returnStdout: true)}"
    GIT_BRANCH = FULL_PATH_BRANCH.substring(FULL_PATH_BRANCH.lastIndexOf('/') + 1, FULL_PATH_BRANCH.length())
  }
 
    stages {
        /* checkout repo */
         stage('configuration') {
            steps {
             script{
                echo 'BRANCH NAME: ' + env.BRANCH_NAME
                echo sh(returnStdout: true, script: 'env')
              echo "#######!!!"
              echo env.GIT_BRANCH
              echo env.FULL_PATH_BRANCH
            }
            }
        }
        
        stage('Checkout SCM') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'main']],
                 userRemoteConfigs: [[
                    url: 'https://github.com/rahuldivakar/testrepo',
                    credentialsId: 'gitpass',
                 ]]
                ])
            }
        }
         stage('Do the deployment') {
            steps {
                sh 'ls'
                echo ">> Run deploy applications "
            }
        }
    }
    post { 
        always { 
            cleanWs()
        }
    }
 
    /* Cleanup workspace */

}
