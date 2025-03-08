# Assignment_2.14
**For activity of creating SQS, SNS, EventBridge, Lambda**

**Does SNS guarantee exactly once delivery to subscribers?**

**Response:** Amazon SNS (Simple Notification Service) does not guarantee exactly-once delivery to subscribers. It provides at-least-once delivery, which means that messages might be delivered more than once. However, SNS FIFO (First-In-First-Out) topics support exactly-once message delivery and processing under certain conditions.

**What is the purpose of the Dead-letter Queue (DLQ)? This is a feature available to SQS/SNS/EventBridge.**

**Response:** A Dead-letter Queue (DLQ) is a special type of message queue that temporarily stores messages that a software system cannot process due to errors. DLQs are useful for debugging and isolating unconsumed messages to determine why processing did not succeed. They help prevent the source queue from overflowing with unprocessed messages and allow for analysis of common fault patterns and potential software problems



Check the logs of the lambda function
 
 ![image](https://github.com/user-attachments/assets/281e2a27-7ca3-4d41-bc4b-3d26fd310d9c)
 ![image](https://github.com/user-attachments/assets/3745b231-f6c2-4887-82f9-3ec6de0ec440)
 ![image](https://github.com/user-attachments/assets/9b603f15-0b01-451b-9469-00c79588f8c3)
 ![image](https://github.com/user-attachments/assets/46ca5566-44c8-44a9-a2a6-1ad5657ffb8a)
 ![image](https://github.com/user-attachments/assets/a89cc1b2-945f-44ed-bbec-33c044a37c43)
 ![image](https://github.com/user-attachments/assets/62d8ced6-2d80-4e3a-a196-9394446be467)

**How would you enable a notification to your email when messages are added to the DLQ?**

Response: To enable email notifications when messages are added to a DLQ, you can use Amazon CloudWatch Alarms. Here are the steps:

Creating a CloudWatch Alarm for a Dead-letter Queue (DLQ) to monitor the "ApproximateNumberOfMessagesVisible" metric is a great way to stay on top of unprocessed messages. Here are the steps to set it up:

****1.**	**Open the CloudWatch Console:
Go to the CloudWatch Console.

**2.**	Create a New Alarm:
In the navigation pane, click on "Alarms" and then "Create Alarm".

**3.**	Select Metric:
- Click on "Select metric" and choose "SQS Metrics".
- Find and select the DLQ you want to monitor.
- Choose the "ApproximateNumberOfMessagesVisible" metric.

**4.**	Configure the Alarm:
- Set the threshold for the alarm. For example, you might want the alarm to trigger when the number of visible messages is greater than 0.
- Configure the period and evaluation criteria according to your needs.
- 
**5.**	Set Actions:
- Choose the actions to take when the alarm state is triggered. You can send a notification to an SNS topic.
If you haven't already, create an SNS topic and subscribe your email address to it.

**6.**	Review and Create:
Review the alarm settings and click "Create alarm".
![image](https://github.com/user-attachments/assets/db8936d9-b9b9-4175-aa49-6cf1fd8e8ea0)


 
Reference: https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/dead-letter-queues-alarms-cloudwatch.html
