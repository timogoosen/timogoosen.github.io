## Boto3 SQS Reader and Writer examples:



Write to SQS Queue
```

#!/usr/bin/env python3 

import boto3 
from faker import Faker
fake = Faker()




# Get the service resource
session = boto3.session.Session(profile_name='testing')
sqs = session.resource('sqs')



# Get the queue
queue = sqs.get_queue_by_name(QueueName='staging-queue')


for x in range(100000000000):

    # Create a new message
    email = fake.email() # Create random fake email
    # 'Lucy Cechtelar'


    response = queue.send_message(MessageBody=email)

    # The response is NOT a resource, but gives you a message ID and MD5
    print(x)
    print(response.get('MessageId'))
    print(response.get('MD5OfMessageBody'))
    ```

```


Reader from the queue:

```

#!/usr/bin/env python3

import boto3
import json

# On ECS:
# Create SQS client
#sqs = boto3.client('sqs')

def get_messages_from_queue(queue_url):
    """Generates messages from an SQS queue.

    Note: this continues to generate messages until the queue is empty.
    Every message on the queue will be deleted.

    :param queue_url: URL of the SQS queue to drain.

    """
    session = boto3.Session(profile_name='testing')
    sqs_client = session.client('sqs')

    while True:
        resp = sqs_client.receive_message(
            QueueUrl=queue_url,
            AttributeNames=['All'],
            MaxNumberOfMessages=10
        )

        try:
            yield from resp['Messages']
        except KeyError:
            return

        entries = [
            {'Id': msg['MessageId'], 'ReceiptHandle': msg['ReceiptHandle']}
            for msg in resp['Messages']
        ]

        resp = sqs_client.delete_message_batch(
            QueueUrl=queue_url, Entries=entries
        )

        if len(resp['Successful']) != len(entries):
            raise RuntimeError(
                f"Failed to delete messages: entries={entries!r} resp={resp!r}"
            )




#queue_url = args['<QUEUE_URL>']
queue_url = "https://sqs.eu-west-1.amazonaws.com/021695320787/staging-queue"


while True:
    for message in get_messages_from_queue(queue_url):
        print(json.dumps(message))   
    
    print("Just print something so it keeps running:")            


```