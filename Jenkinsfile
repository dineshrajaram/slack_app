pipeline {
    stages {
         stage("checkout SCM") {
            steps {
                echo 'Hrllo'
                slackSend botUser: true, channel: '#test-automation', color: 'green', message: 'Test message', teamDomain: 'https://dineshworkspace-group.slack.com', tokenCredentialId: 'd9f15e7e-61af-4f92-a005-f00b6be4cb0a'
            }
         }
    }
}
