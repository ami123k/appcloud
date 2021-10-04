 pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '67c2744e-c2d9-4b17-9f12-35c2d4eaac32',
                            url: 'https://github.com/ami123k/appcloud.git']]])
                }
            }
        }
    }
 }
