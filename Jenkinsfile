def getDetails(){
    return ["$env.RUN_TESTS_DISPLAY_URL","$env.BUILD_NUMBER","$currentBuild.durationString"]
}
def notifySlack(total,passed,failed){
                blocks =
                [
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
                                    "text": "*Environment\t\t:* \t $env.RUN_TESTS_DISPLAY_URL "
                                ],
                                [
                                    "type": "mrkdwn",
                                    "text": "*Test Type\t\t\t :* \t regression "
                                ],
                                [
                                    "type": "mrkdwn",
                                    "text": "*Build Number \t :*\t $BUILD_NUMBER"
                                ],
                                [
                                    "type": "mrkdwn",
                                    "text": "*Build Duration\t:* \t $currentBuild.durationString"
                                ]
                            ]
                        ],
                        [
                            "type": "section",
                            "fields": [
                                [
                                    "type": "mrkdwn",
                                    "text": "*Total Tests:* total"
                                ],
                                [
                                    "type": "mrkdwn",
                                    "text": " "
                                ],
                                [
                                    "type": "mrkdwn",
                                    "text": "*Passed:* passed"
                                ],
                                [
                                    "type": "mrkdwn",
                                    "text": "*Failed:* failed"
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
pipeline {
    agent any
    stages {
         stage("Build Stage") 
            {
            steps {
                script {
                    echo 'Hello'
                    sleep	10
                }
            }
			post {
                always{
					def stats = junit 'results/xunitlog.xml'
                    notifySlack(stats.totalCount,stats.passCount,stats.failCount)
                }
            }
        }
}
