## BOTO3 SNS Publish example with Profile

```
#!/usr/bin/env python3
import json
import boto3

message = {"command": "BuildAlert",  "channel": "#test-slack-notify","project":"testing","branch":"master", "build_number":"31", "url":"https://jenkins.url.com/blue/organizations/jenkins/test-suite/activity", "status": "started" }


session = boto3.Session(profile_name='test')
client = session.client('sns')

response = client.publish(
    TargetArn="arn:aws:sns:eu-west-1:redacted-account-id:test-slacker.fifo",
    Message=json.dumps({'default': json.dumps(message)}),
    MessageStructure='json',MessageDeduplicationId='someproject',
    MessageGroupId='110-results'
)


```