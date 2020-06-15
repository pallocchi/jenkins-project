@Library('jenkins-scripts')_

stage('Pull') {
    checkout([
     $class: 'GitSCM',
     branches: [[name: 'master']],
     userRemoteConfigs: [[
        url: 'https://github.com/pallocchi/jenkins-project.git',
        credentialsId: '',
     ]]
    ])
}

stage('Test') {
    test
}

stage('Deploy') {
    deploy "HelloWorld.app"
}