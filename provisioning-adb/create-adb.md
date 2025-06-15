
# Create and Manage Autonomous Database

## Introduction

An Autonomous Database (ADB) resource is a user database. You can create many Autonomous Databases in a single Autonomous Container Database resource. For an overview of Autonomous Databases, their features, and how to use them, see [About Autonomous Database](https://docs.oracle.com/en/cloud/paas/autonomous-database/dedicated/aadvv/index.html).

This lab walks you through the steps to provision and manage Autonomous Database. 

Estimated Time: 30 minutes


### Objectives

As a database user, DBA or application developer:

1. Rapidly deploy an Autonomous databases.

### Required Artifacts

- A pre-provsioned ODB Network
- A pre-provsioned Oracle Exadata Infrastructure
- A pre-provsioned Autonomous VM Cluster
- A pre-provisioned Autonomous Container Database

## Task 1: Create Autonomous Database

In this section, you will be provisioning an Autonomous database using the Azure portal.

1.	- Autonomous Database creation is managed from the OCI Console. From your AVMC details page in AWS, click “Manage in OCI” and log in to your OCI tenancy.

  ![Manage in OCI](./images/manageinoci.png " ")

- Click on Oracle Database from the OCI Menu, and select Autonomous Database on Dedicated infrastructure.

  ![This image shows the result of performing the above step.](./images/adbd.png " ")

- Expand the Menu and select Autonomous Database.

  ![This image shows the result of performing the above step.](./images/adb.png " ")

- ADB Details page lists all the avialable Autonomous Databases in the selected Compartment.

  ![This image shows the result of performing the above step.](./images/adb1.png " ")

- Click Create Autonomous Database to provision a new ADB. Enter a Display Name, Database name, Select a Compartment,and the Workload type. You can configure your database in two different modes based on the workload type, as: Autonomous Data Warehouse and Autonomous Transaction Processing. Click [here](https://docs.oracle.com/en/cloud/paas/autonomous-database/dedicated/adbaa/index.html#articletitle) to learn more about Workload types supported in Autonomoud Database.

  ![This image shows the result of performing the above step.](./images/createadb.png " ")

- Select the Autonomous Container Database (ACD) in which you want to provision ADB. You can also filter Autonomous Data Guard-enabled ACDs. 

  ![This image shows the result of performing the above step.](./images/createadb1.png " ")

- Under the Database configuration, enter the number of CPUs and amount of Storage you require for the database. 
    
    Autonomous Database for Developers instances are free Autonomous Databases that developers can use to build and test new applications.
    With Autonomous Database for Developers instances, you can try new Autonomous Database features for free and apply them to ongoing or new development projects. Developer database comes with limited resources and is, therefore, not suitable for large-scale testing and production deployments. When you need more compute or storage resources, you can transition to a paid database licensing by cloning your developer database into a regular Autonomous Database. Learn more about [Autonomous Database for Developers](https://docs.oracle.com/en/cloud/paas/autonomous-database/dedicated/eddjo/).

    Auto scaling enables a database to use up to three times more CPU and IO resources than its specified CPU count. When auto scaling is enabled, if your workload requires additional CPU and IO resources the database automatically uses the resources without any manual intervention required. Learn more about [Enable or Disable Auto Scaling](https://docs.oracle.com/en/cloud/paas/autonomous-database/dedicated/adban/index.html).

    ![This image shows the result of performing the above step.](./images/createabd2.png " ")

- Optionally, you can also Enable Elatic Pool for the ADB. 
   
    Use an elastic pool to consolidate your Autonomous Database instances, in terms of their allocation of compute resources, and to provide up to 87% cost savings. 
    Elastic pools help you improve operating efficiency and reduce costs by bringing all of your databases to the Cloud. This also supports consolidating resources and simplifying administration and operations by using Autonomous Database. When you need a large number of databases, that can scale up and down elastically without downtime, you can benefit by creating and using elastic pools. Learn more about [Elastic Pools](https://docs.oracle.com/en/cloud/paas/autonomous-database/dedicated/catiu/index.html#articletitle).

  ![This image shows the result of performing the above step.](./images/createadb3.png " ")

- Enter the Administrator credentials. Username for all Autonomous database will be ADMIN. Specify the password for the instance. 

  ![This image shows the result of performing the above step.](./images/createadb4.png " ")

- You can Configure Database-level network access by clicking Modify Access Control button.

    ![This image shows the result of performing the above step.](./images/createadb5.png " ")

    ![This image shows the result of performing the above step.](./images/createadb6.png " ")

- Enter customer contact information to receive operational notifications and announcements.
    
    ![This image shows the result of performing the above step.](./images/createadb7.png " ")

- Click on Advanced Options to view Encryption Key used, select Character set and National character set, to Enable Database In-Memory and add Tags.

    ![This image shows the result of performing the above step.](./images/createadb8.png " ")

- Click Create Autonomous Database to start provisioning the instance.

    ![This image shows the result of performing the above step.](./images/createadb9.png " ")

- Your autonomous database instance should be up and running in a few minutes.

- Once provisioned, you can click on the instance name to see instance details.

    ![This image shows the result of performing the above step.](./images/createad10.png " ")


## Task 2: Manage Autonomous Database

- 











## Acknowledgements

*All Done! You have successfully created Autonomous Database.*

- **Author** - Tejus Subrahmanya, Principal Product Manager, Autonomous Database 

- **Last Updated By/Date** - Tejus Subrahmanya, June 2025