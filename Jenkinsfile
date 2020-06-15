properties([pipelineTriggers([githubPush()])])

libraries {
  lib('jenkins-scripts')
}

pipeline {
    agent any
    stages {
        stage('Pull') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'master']],
                 userRemoteConfigs: [[
                    url: 'https://github.com/pallocchi/jenkins-project.git',
                    credentialsId: '',
                 ]]
                ])
            }
        }
        stage('Test') {
            steps {
                test
            }
        }
        stage('Deploy') {
            steps {
                deploy "HelloWorld.app"
            }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}