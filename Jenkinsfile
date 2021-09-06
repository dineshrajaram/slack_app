pipeline {
    agent any
    stages {
         stage("checkout SCM") {
            steps {
                echo 'Hello'
		blocks = [
			[
				"type": "section",
				"text": [
					"type": "mrkdwn",
					"text": "Hello, Assistant to the Regional Manager Dwight! *Michael Scott* wants to know where you'd like to take the Paper Company investors to dinner tonight.\n\n *Please select a restaurant:*"
				]
			],
			[
				"type": "divider"
			],
			[
				"type": "section",
				"text": [
					"type": "mrkdwn",
					"text": "*Farmhouse Thai Cuisine*\n:star::star::star::star: 1528 reviews\n They do have some vegan options, like the roti and curry, plus they have a ton of salad stuff and noodles can be ordered without meat!! They have something for everyone here"
				],
				"accessory": [
					"type": "image",
					"image_url": "https://s3-media3.fl.yelpcdn.com/bphoto/c7ed05m9lC2EmA3Aruue7A/o.jpg",
					"alt_text": "alt text for image"
				]
			]
		]
	    	slackSend(botUser: true, channel: '#test-automation', color: 'green', blocks: blocks , teamDomain: 'https://dineshworkspace-group.slack.com', tokenCredentialId: 'd9f15e7e-61af-4f92-a005-f00b6be4cb0a')
            }
         }
    }
}
