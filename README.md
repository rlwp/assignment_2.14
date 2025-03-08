# Assignment_2.14
For activity of creating SQS, SNS, EventBridge, Lambda
Does SNS guarantee exactly once delivery to subscribers?
Response: Amazon SNS (Simple Notification Service) does not guarantee exactly-once delivery to subscribers. It provides at-least-once delivery, which means that messages might be delivered more than once. However, SNS FIFO (First-In-First-Out) topics support exactly-once message delivery and processing under certain conditions2.
What is the purpose of the Dead-letter Queue (DLQ)? This is a feature available to SQS/SNS/EventBridge.
Response: A Dead-letter Queue (DLQ) is a special type of message queue that temporarily stores messages that a software system cannot process due to errors. DLQs are useful for debugging and isolating unconsumed messages to determine why processing did not succeed4. They help prevent the source queue from overflowing with unprocessed messages and allow for analysis of common fault patterns and potential software problems
How would you enable a notification to your email when messages are added to the DLQ?
Response: To enable email notifications when messages are added to a DLQ, you can use Amazon CloudWatch Alarms. Here are the steps:
1.	Create a CloudWatch Alarm for the DLQ to monitor the "ApproximateNumberOfMessagesVisible" metric.
2.	Set the threshold for the alarm to trigger when the number of messages in the DLQ exceeds a certain value.
3.	Configure the alarm to send a notification to an Amazon SNS topic.
4.	Subscribe your email address to the SNS topic to receive notifications

Check the logs of the lambda function
 
 
 

 

 
 

This is to create the alarm state for the DLQ
Creating a CloudWatch Alarm for a Dead-letter Queue (DLQ) to monitor the "ApproximateNumberOfMessagesVisible" metric is a great way to stay on top of unprocessed messages. Here are the steps to set it up:
1.	Open the CloudWatch Console:
Go to the CloudWatch Console.
2.	Create a New Alarm:
In the navigation pane, click on "Alarms" and then "Create Alarm".
3.	Select Metric:
Click on "Select metric" and choose "SQS Metrics".
Find and select the DLQ you want to monitor.
Choose the "ApproximateNumberOfMessagesVisible" metric.
4.	Configure the Alarm:
Set the threshold for the alarm. For example, you might want the alarm to trigger when the number of visible messages is greater than 0.
Configure the period and evaluation criteria according to your needs.
5.	Set Actions:
Choose the actions to take when the alarm state is triggered. You can send a notification to an SNS topic.
If you haven't already, create an SNS topic and subscribe your email address to it.
6.	Review and Create:
Review the alarm settings and click "Create alarm".

 
Reference: https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/dead-letter-queues-alarms-cloudwatch.html
