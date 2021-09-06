def setEnvironment(){
    if (env.BRANCH_NAME == "main") {
    return 'stage'; 
  } else {
    return 'dev' 
  }
}
pipeline {
    agent any
    stages {
         stage("checkout SCM") {
            steps {
		    script {
			    echo 'Hello'
			    def env = setEnvironment()
			    blocks = [
				    [
					    "type": "section",
					    "text": [
						    "type": "mrkdwn",
						    "text": "*:white_check_mark:Test Execution Complete!*"
					    ]
				    ],
				    [
					    "type": "section",
					    "fields": [
						    [
							    "type": "mrkdwn",
							    "text": "*Environment\t\t:* \t $env.BRANCH_NAME "
						    ],
						    [
							    "type": "mrkdwn",
							    "text": "*Test Type\t\t\t :* \t regression "
						    ],
						    [
							    "type": "mrkdwn",
							    "text": "*Build Number \t :*\t $env.BUILD_NUMBER"
						    ],
						    [
							    "type": "mrkdwn",
							    "text": "*Build Duration\t:* \t $currentBuild.duration"
						    ]
					    ]
				    ],
				    [
					    "type": "section",
					    "fields": [
						    [
							    "type": "mrkdwn",
							    "text": "*Total Tests:* 100"
						    ],
						    [
							    "type": "mrkdwn",
							    "text": " "
						    ],
						    [
							    "type": "mrkdwn",
							    "text": "*Passed:* 99"
						    ],
						    [
							    "type": "mrkdwn",
							    "text": "*Failed:* 1"
						    ]
					    ]
				    ],
				    [
					    "type": "actions",
					    "elements": [
						    [
							    "type": "button",
							    "text": [
								    "type": "plain_text",
								    "text": "Test Report"
							    ],
							    "value": "click_me_123",
							    "action_id": "actionId-0",
							    "url": "https://www.google.com"
						    ]
					    ]
				    ]
			    ]
			    slackSend(botUser: true, channel: '#test-automation', color: 'green', blocks: blocks , teamDomain: 'https://dineshworkspace-group.slack.com', tokenCredentialId: 'd9f15e7e-61af-4f92-a005-f00b6be4cb0a')
		    }
	    }
	 }
    }
}
