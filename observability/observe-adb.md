# Oracle Database@AWS — Observability with AWS Native Services

## Introduction
Welcome to this hands-on lab on Oracle Database@AWS. This lab focuses on the native integration with AWS for database observability and event handling. We will explore how metrics from your Autonomous Database are surfaced in AWS CloudWatch, how to build monitoring dashboards, how to set up proactive alarms, and how to capture database lifecycle events using Amazon EventBridge.

This workshop is designed for cloud engineers, database administrators, and DevOps professionals who want to manage their Oracle Database@AWS workloads using familiar AWS native tools.

Estimated Time: 30 minutes

### Objectives
In this lab, you will learn how to:

- Locate and explore Oracle Database@AWS performance metrics within AWS CloudWatch.
- Build custom AWS CloudWatch Dashboards to visualize key database health and performance indicators.
- Configure CloudWatch Alarms to proactively notify you of potential issues based on database metrics.
- Use Amazon EventBridge to capture database events (e.g., start, stop, backup completion).
- Route database events to AWS CloudWatch Logs for centralized logging and analysis.

### Prerequisites
- An Oracle Database@AWS environment must be pre-provisioned. This lab does not cover the provisioning of the network, Exadata Infrastructure, or the Autonomous Database itself. For detailed instructions on provisioning, please complete the [Oracle Database@AWS- Autonomous Database on dedicated infrastructure](https://livelabs.oracle.com/pls/apex/r/dbpm/livelabs/view-workshop?wid=4203) LiveLab first.
- Familiarity with Oracle Database concepts.
- Basic understanding of the AWS Management Console, specifically CloudWatch and EventBridge.


## Lab 1: Exploring Database Metrics in AWS CloudWatch

### Introduction
Oracle Database@AWS - Autonomous Database on Dedicated Infrastructure automatically publishes a rich set of performance and health metrics directly to AWS CloudWatch. This allows you to monitor your database using the same tools you use for the rest of your AWS infrastructure. In this lab, you'll learn how to find and analyze these metrics.

### Tasks
1. Navigate to the **AWS CloudWatch** service.  
2. Find the **OracleDatabase@AWS** custom metric namespace.  
3. Explore the available metrics and their dimensions (e.g., `dbName`, `dbId`).  
4. Graph a key metric like **CPUUtilization** to view its recent activity.


## Lab 2: Visualizing Performance with CloudWatch Dashboards

### Introduction
While viewing individual metrics is useful, a dashboard provides a consolidated, at-a-glance view of your database's health. In this lab, you will create a custom CloudWatch Dashboard to monitor the most important metrics for your database.

### Tasks
1. Create a new **CloudWatch Dashboard**.  
2. Add a widget to display the **CPUUtilization** metric.  
3. Add widgets for other key metrics, such as **StorageUtilization** and **SessionCount**.  
4. Customize the layout and widget types for clarity.


## Lab 3: Proactive Monitoring with CloudWatch Alarms

### Introduction
Dashboards are great for observing performance, but alarms are essential for proactive management. CloudWatch Alarms can automatically notify you when a metric crosses a defined threshold, allowing you to respond to potential issues before they impact users.

### Tasks
1. Select a metric to create an alarm for (e.g., **CPUUtilization**).  
2. Configure the alarm conditions (e.g., trigger when CPU is **above 80% for 5 minutes**).  
3. Create a new **Amazon SNS (Simple Notification Service)** topic to send notifications.  
4. Create the alarm and confirm your SNS email subscription.  
5. *(Optional)* Temporarily lower the alarm threshold to test the notification flow.


## Lab 4: Capturing Events with Amazon EventBridge and CloudWatch Logs

### Introduction
Beyond metrics, your database emits important lifecycle and state-change events. Oracle Database@AWS sends these events to **Amazon EventBridge**, allowing you to build event-driven automations. A common use case is to log all events for auditing and analysis.

### Tasks
1. Navigate to the **Amazon EventBridge** service.  
2. Create a new rule that listens for events from the `aws.oracle` source.  
3. Define an event pattern to capture all events from your database.  
4. Configure **AWS CloudWatch Logs** as the target for the rule.  
5. Perform an action on your database (e.g., stop and start it) and verify that the corresponding events appear in your CloudWatch Log stream.

## Acknowledgements

- **Author** - German Viscuso, Director of Developer Community, Autonomous Database

- **Last Updated By/Date** - German Viscuso, September 2025

