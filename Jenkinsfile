properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
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
        stage('Unit & Integration Tests') {
            steps {
                script {
                    sh './gradlew clean test --no-daemon'
                }
            }
        }
        stage('Do the deployment') {
            steps {
                echo ">> Run deploy applications "
            }
        }
    }

    /* Cleanup workspace */
    post {
       always {
           deleteDir()
       }
   }
}