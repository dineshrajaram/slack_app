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
						"text": "*Environment\t\t:* \t Dev "
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
						"text": "*Build Duration\t:* \t ${currentBuild.durationString.minus(' and counting')}"
					]
				]
			],
			[
				"type": "section",
				"fields": [
					[
						"type": "mrkdwn",
						"text": "*Total Tests:* $total"
					],
					[
						"type": "mrkdwn",
						"text": " "
					],
					[
						"type": "mrkdwn",
						"text": "*Passed:* $passed"
					],
					[
						"type": "mrkdwn",
						"text": "*Failed:* $failed"
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
							"text": "Jenkins Test Stats"
						],
						"value": "click_me_123",
						"action_id": "actionId-0",
						"url": "$RUN_TESTS_DISPLAY_URL"
					],
					[
						"type": "button",
						"text": [
							"type": "plain_text",
							"text": "rbf Test Report"
						],
						"value": "click_me_123",
						"action_id": "actionId-1",
						"url": "$BUILD_URL/artifact/xunitlog.xml"
					]
				]
			]
		]
	slackSend(botUser: true, channel: 'dce_qa', blocks: blocks , teamDomain: 'https://dnb-it.slack.com', tokenCredentialId: 'rbf-qa-bot')
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
// 					script{
// 						def stats = junit 'xunitlog.xml'
// 						echo "$stats"
// // 						notifySlack(stats.totalCount,stats.passCount,stats.failCount)
// 					}
					archiveArtifacts artifacts: '*.xml', fingerprint: true
					archiveArtifacts artifacts: '*.html', fingerprint: true
					publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'log.html', reportName: 'HTML Report', reportTitles: ''])
				}
			}
		}
	}
}
