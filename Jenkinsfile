pipeline {
    stages {
         stage("checkout SCM") {
            steps {
               slackSend token: '', channel: 'dce_qa', message: 'Build Status: ${currentBuild.currentResult} ${env.BUILD_NUMBER}'
            }
         }
    }
}
