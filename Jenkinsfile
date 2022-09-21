
 
pipeline {
    /* specify nodes for executing */
    agent any
 
    stages {
        /* checkout repo */
         stage('configuration') {
            steps {
                echo 'BRANCH NAME: ' + env.BRANCH_NAME
                echo sh(returnStdout: true, script: 'env')
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
