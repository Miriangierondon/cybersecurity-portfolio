<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Security Monitoring System

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-monitoring)

**Author:** Miriangie Rondon  
**Email:** miriangier12@gmail.com

---

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_reghtjy)

---

## Introducing Today's Project!

in this project we are creating a secret and securing it on secrets manager, we are monitoring it with cloudtrail and getting notifications through sns

### Tools and concepts

Services I used were:
AWS Secrets Manager, AWS CloudWatch, AWS CloudTrail, AWS SNS, AWS IAM and AWS S3. Key Concepts learned include secret storing, CloudWatch vs CloudTrail, SNS Notifications and endpoints, how to create CloudWatch alarms and filters. 

### Project reflection

This project took me approximately 3 hours. he most challenging part was troubleshooting why the email wasn't delived in first test since there were no error messages/logs. It was a good experience to compare CloudTrail and SNS notifications since it allowed me to see why we had to use CloudWatch and alarms.

---

## Create a Secret

AWS Secrets Manager helps you protect secrets, which are passwords, API keys, credentials and sensitive information. Instead of storing important credentials in your code or sharing them via email, you can tuck them safely away in Secrets Manager.

To set up for my project, I created a secret called TopSecret that contains I need to play volleyball to function.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_o5p6q7r8)

---

## Set Up CloudTrail

AWS CloudTrail is a monitoring service - think of it as an activity recorder throughout your AWS account. It documents every action taken, like who did what, when they did it, and where they did it from.

A trail tells CloudTrail exactly what activity to record and where to save those recordings. When you create a trail, you're essentially saying "Hey CloudTrail, please keep track of all xyz activities and store the data in this specific location." a trail to...

CloudTrail events include types like management, insight, data and network activity events. In this project we are set up our trail to be a Management Event since accessing a secret falls into that category.

### Read vs Write Activity

Read API activity involves viewing something and Write API activity involves create, delete or edit something and For this project, we checked both to learn about both kind of activities but we really only need write activity.

---

## Verifying CloudTrail

The two ways I retrieved my secret were through the AWS Management Console and the AWS CLI; the console allowed me to view the secret directly in the Secrets Manager interface, while the CLI allowed me to retrieve it by running a command such as aws secretsmanager get-secret-value

To analyze my CloudTrail events, I visited event history and I found the event that says we got our event and This tells me that the secret was access and seen.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_s8t9u0v1)

---

## CloudWatch Metrics

CloudWatch Logs is a monitoring service that brings together many services and helps us analyze and create alarms. It's important for monitoring because you get to create insights and get alerted about events.

CloudTrail records AWS API activity (who did what in AWS).
CloudWatch stores operational logs and metrics from applications and services.

A CloudWatch metric is a numerical measurement used to monitor the performance or activity of AWS resources over time; when setting up a metric, the metric value represents the number recorded when a log event matches the filter pattern, and the default value is used when no matching events occur during a time period so the metric still records a value.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_a9b0c1d2)

---

## CloudWatch Alarm

A CloudWatch alarm is a feature that sets off an alarm which will notify us something is going on, I set my CloudWatch alarm threshold to be how many times the GetSecretValue event happens in 5 minutes period so the alarm triggers when the average number is 1.

I created an SNS topic along the way. An SNS topic is like a broadcast channel. My SNS topic is set up tosend us an email when our secret is accessed.

AWS requires email confirmation because we don't want to automatically send email to any address. This helps prevent sending unwanted emails to recipients.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_fsdghstt)

---

## Troubleshooting Notification Errors

To test my monitoring system, I retrieved my secret The results were negatives. My email didn't receive any notification.

When troubleshooting the notification issues I investigated if CloudTrail wasn't recording the GetSecretValue event.
If CloudTrail wasn't sending logs to CloudWatch.
If CloudWatch's metric filter wasn't filtering logs correctly.
If CloudWatch's Alarm wasn't triggering an action.
If SNS wasn't delivering emails to you

I initially didn't receive an email before because i didn't have the right threshold. The key solution was switch from average to sum

---

## Success!

To validate all my settings and I finally received an email.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_ageraergearge)

---

## Comparing CloudWatch with CloudTrail Notifications

In a project extension, I updated my configurations to get a better comparison of CloudTrail SNS notifications and CloudWatch alarms.

After enabling CloudTrail SNS notifications, my inbox quickly filled with a large number of emails. While it was useful to know that activity was occurring in my AWS account, the notifications often lacked clear context about what exactly had happened. Because of this, it was sometimes difficult to quickly understand the significance of each event, and the high volume of alerts could become overwhelming. This highlighted the importance of refining monitoring rules and alerts so that notifications are more targeted, informative, and easier to act upon.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-monitoring_d7e8f9g0)

---

---
