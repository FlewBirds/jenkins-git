pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too "
                    ls -lah && ls -lrt /tmp
                '''
            }
        }
    }
}
----
pipeline{
    post {
        always {
            echo 'Cleaning up workspace'
        }
        success {
            slackSend (color: 'GREEN', message: \
                "${env.JOB_NAME} Successful build")
        }
        failure {
            slackSend (color: 'RED', message: "${env.JOB_NAME} Failed build")
        }
    }
    agent{

        node {
            label("docker")
            customWorkspace "/opt/workspace"
        }
    }
    environment{
        TARGET_HOST_IP   = "${params.TARGET_HOST_IP}"
    }

    stages{
        stage('Validation'){
            steps{
                script{
                    try{
                        sh 'docker ps'
                    }catch (Exception e) {
                        echo 'Exception Occurred' + e.toString()
                        error("Deplyment Failed as Docker service doesnot exists or not running on ${TARGET_HOST_IP}")
                    }
                }
            }
        }
      stage('Checkout Common Config Repo'){
          steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/{GIT_BRANCH}}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '803e-b03c4ff64b81', url:'https://dat.mydummies.com/git/scm/da/ds-common-configuration.git']]])
          }
      }
        stage("My First Pipeline"){
            steps{
                sh '''
                   echo "Hello This is my First Pipeline"
                    touch testfile
                    ls -lrth
                    '''
            }
        }
    }
}
