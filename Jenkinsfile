properties([pipelineTriggers([githubPush()])])

@Library('jenkins-scripts') _

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
                script {
                    test false
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    deploy "HelloWorld.app"
                }
            }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}