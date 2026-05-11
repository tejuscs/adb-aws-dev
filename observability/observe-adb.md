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
- Familiarity with available ADB-D Metrics on AWS: https://docs.oracle.com/en-us/iaas/Content/database-at-aws-exadata-awsmn/awsmn-monitor-cloudwatch.html

## Task 1: Exploring Database Metrics in AWS CloudWatch

### Introduction
Oracle Database@AWS - Autonomous Database on Dedicated Infrastructure automatically publishes a rich set of performance and health metrics directly to AWS CloudWatch. This allows you to monitor your database using the same tools you use for the rest of your AWS infrastructure. In this task, you'll learn how to find and analyze these metrics.

### Steps
1. Navigate to the **AWS CloudWatch** service.  

![This image shows the result of performing the above step.](./images/1_1.png " ")

![This image shows the result of performing the above step.](./images/1_2.png " ")

2. Find the **OracleDatabase@AWS** custom metric namespaces.

![This image shows the result of performing the above step.](./images/1_3.png " ")

3. Within **OracleDatabase@AWS** custom metric namespaces find the Autonomous Database metrics

![This image shows the result of performing the above step.](./images/1_4.png " ")

4. Explore the available metrics and their dimensions (e.g., `dbName`, `dbId`).

![This image shows the result of performing the above step.](./images/1_5.png " ")

5. Graph a key metric like **CPUUtilization** to view its recent activity.

![This image shows the result of performing the above step.](./images/1_6.png " ")

![This image shows the result of performing the above step.](./images/1_7.png " ")

6. Change the time granularity in the graph

![This image shows the result of performing the above step.](./images/1_8.png " ")

## Task 2: Visualizing Performance with CloudWatch Dashboards

### Introduction
While viewing individual metrics is useful, a dashboard provides a consolidated, at-a-glance view of your database's health. In this task, you will create a custom CloudWatch Dashboard to monitor the most important metrics for your database.

### Steps
1. Create a new **CloudWatch Dashboard**.  

![This image shows the result of performing the above step.](./images/2_0.png " ")

![This image shows the result of performing the above step.](./images/2_1.png " ")

![This image shows the result of performing the above step.](./images/2_2.png " ")

![This image shows the result of performing the above step.](./images/2_3.png " ")

2. Add a widget to display the **CPUUtilization** metric.

![This image shows the result of performing the above step.](./images/2_4.png " ")

![This image shows the result of performing the above step.](./images/2_9.png " ")

3. Add widgets for other key metrics, such as **StorageUtilization** and **Sessions**.

![This image shows the result of performing the above step.](./images/2_10.png " ")

![This image shows the result of performing the above step.](./images/2_6.png " ")

![This image shows the result of performing the above step.](./images/2_9.png " ")

![This image shows the result of performing the above step.](./images/2_10.png " ")

![This image shows the result of performing the above step.](./images/2_7.png " ")

![This image shows the result of performing the above step.](./images/2_9.png " ")

4. View the Dashboard

![This image shows the result of performing the above step.](./images/2_8.png " ")

## Task 3: Proactive Monitoring with CloudWatch Alarms

### Introduction
Dashboards are great for observing performance, but alarms are essential for proactive management. CloudWatch Alarms can automatically notify you when a metric crosses a defined threshold, allowing you to respond to potential issues before they impact users.

### Steps
1. Select a metric to create an alarm for (e.g., **CPUUtilization**).

Do Steps 1 to 5 in Task 1 above and then click on the "Create alarm" button.


![This image shows the result of performing the above step.](./images/3_3.png " ")

2. Configure the alarm conditions (e.g., trigger when CPU is **above 80% utilization for 5 minutes**).  

![This image shows the result of performing the above step.](./images/3_5.png " ")

![This image shows the result of performing the above step.](./images/3_6.png " ")

3. Create a new **Amazon SNS (Simple Notification Service)** topic to send notifications.

![This image shows the result of performing the above step.](./images/3_8.png " ")

![This image shows the result of performing the above step.](./images/3_9.png " ")

![This image shows the result of performing the above step.](./images/3_10.png " ")

4. Create the alarm, confirm your SNS email subscription and get the alarm notification when fired.

![This image shows the result of performing the above step.](./images/3_11.png " ")

![This image shows the result of performing the above step.](./images/3_12.png " ")

![This image shows the result of performing the above step.](./images/3_13.png " ")

![This image shows the result of performing the above step.](./images/3_14.png " ")

![This image shows the result of performing the above step.](./images/3_16.png " ")

5. *(Optional)* Temporarily lower the alarm threshold to test the notification flow (you'd get an e-mail like the one below)

![This image shows the result of performing the above step.](./images/3_17.png " ")

## Task 4: Capturing Events with Amazon EventBridge and CloudWatch Logs

### Introduction
Beyond metrics, your database emits important lifecycle and state-change events. Oracle Database@AWS sends these events to **Amazon EventBridge**, allowing you to build event-driven automations. A common use case is to log all events for auditing and analysis.

### Steps
1. Navigate to the **Amazon EventBridge** service.

![This image shows the result of performing the above step.](./images/4_2.png " ")

![This image shows the result of performing the above step.](./images/4_3.png " ")

2. Create a new rule that listens for events from the `odb` event bus.

![This image shows the result of performing the above step.](./images/4_4.png " ")

3. Define an event pattern to capture all events from your database.

![This image shows the result of performing the above step.](./images/4_7.png " ")

Select `AWS services`, `Oracle Database@AWS` and `All Events` in the drop downs. Click on `Edit pattern`.

![This image shows the result of performing the above step.](./images/4_8.png " ")

Enter a custom event pattern in JSON format with the same event bus and the autonomous database service prefix (`com.oraclecloud.databaseservice.autonomous`)

![This image shows the result of performing the above step.](./images/4_5.png " ")

4. Configure **AWS CloudWatch Logs** as the target for the rule (here we create a new log group but you can also choose an existing one if available).

![This image shows the result of performing the above step.](./images/4_10.png " ")

![This image shows the result of performing the above step.](./images/4_11.png " ")

The final screen before rule creation should look like this:

![This image shows the result of performing the above step.](./images/4_12.png " ")

![This image shows the result of performing the above step.](./images/4_13.png " ")

5. (Optional) Perform an action on your database (e.g., stop and start it) and verify that the corresponding events appear in your CloudWatch Log stream.

## Acknowledgements

- **Author** - German Viscuso, Director of Developer Community, Autonomous Database

- **Last Updated By/Date** - German Viscuso, October 2025

