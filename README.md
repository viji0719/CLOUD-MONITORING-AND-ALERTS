# CLOUD-MONITORING-AND-ALERTS

**COMPANY** : CODETECH IT SOLUTIONS

**NAME** : PRAGATHI P

**INTERN ID** : CT04DG1065

**DOMAIN** :Cloud Computing

**DURATION** : 4 WEEKS

**MENTOR** :Neela Santhosh Kumar

**DESCRIPTION**

Cloud monitoring and alerts are essential for managing and maintaining cloud-based infrastructure. In this task, I implemented a basic yet functional monitoring system using **AWS CloudWatch**, focusing specifically on tracking the **CPU utilization** of an Amazon EC2 instance. This included setting up an alarm to notify when CPU usage exceeded a certain threshold and simulating a high-load situation to test the alert mechanism in real time.

 **Objective**
The objective of this activity was to:
* Launch a cloud-based compute resource (EC2 instance)
* Monitor the CPU utilization of that instance using AWS CloudWatch
* Set up an alarm to detect high CPU usage
* Configure an alert system to notify when thresholds were breached
* Simulate a CPU spike to trigger the alarm and validate the monitoring setup

**Implementation**

1. **Launching an EC2 Instance**

To begin, I launched a **t2.micro EC2 instance** using the **Amazon Linux 2023 AMI**, which is free tier eligible. Basic configuration was done through the AWS Management Console, including selecting the appropriate instance type, defining key pairs, and configuring security group rules to allow SSH access. Once the instance was in a running state, it acted as a test environment for monitoring CPU usage.

 3. **Setting Up CloudWatch Alarm for CPUUtilization**
    
The next step was configuring a monitoring alarm using **Amazon CloudWatch**. I selected the **CPUUtilization** metric under EC2 > Per-Instance Metrics. This metric helps monitor how much of the instance’s processing capacity is being used.
An alarm was created with the following configuration:
**Metric:** CPUUtilization
**Condition:** Greater than 80% usage
**Evaluation Period:** 1 data point (1 minute)
**Alarm Name:** HighCPUUtilizationAlarm
The alarm was associated with an **Amazon SNS Topic** (Simple Notification Service), which was set to send an email notification when the threshold condition was met. My email was subscribed to the topic and confirmed via a verification link sent to my inbox.

 3. **Simulating a CPU Spike**

To trigger the alarm, I connected to the EC2 instance using **EC2 Instance Connect** and ran a CPU-intensive command using the `stress` tool.

sudo yum install stress -y
stress --cpu 2 --timeout 300

This command simulated a high CPU load for 5 minutes by running two CPU workers, enough to push the usage beyond 80%.

4. **Receiving and Observing Alerts**
   
After a short delay, the CPUUtilization crossed the threshold, and the alarm transitioned from `OK` to `ALARM` state. This change triggered an email alert, confirming the successful working of the monitoring and alert system. The email contained the alarm name and the timestamp of the event, proving the system's real-time responsiveness.

6. **Visual Confirmation (Optional)**
   
Though not mandatory, I also verified the alarm status visually by revisiting the CloudWatch console. The alarm’s state change was clearly shown, confirming that CloudWatch had successfully detected and responded to the CPU spike.

**Conclusion**

This task provided a hands-on understanding of how to set up **basic cloud monitoring and alerts** using AWS services. By focusing on **CPU utilization**, a commonly tracked metric in cloud environments, the activity demonstrated how administrators can receive timely alerts about performance issues. AWS CloudWatch and SNS together offer an efficient, scalable solution for real-time monitoring and notification, which is essential for maintaining system health and preventing downtime.

