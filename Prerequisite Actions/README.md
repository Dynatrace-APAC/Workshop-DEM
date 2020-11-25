# Prerequisites Actions for the Dynatrace DEM Workshop 

## Dynatrace Accounts and AWS EC2 Access

You'll need to have the following access:

* Dynatrace SaaS/Managed Account. Get your free SaaS trial [here](https://www.dynatrace.com/trial/).
* AWS account, with the ability to create an EC2 instance from a public AMI. Signup to a free trial [here](https://aws.amazon.com/free/).

## EC2 Setup

The following conatins the instructions to create the easyTravel application which will be used duing the DEM workshop.

Access your AWS console and navigate to the **EC2** service.

Select **Instances** > **Launch Instance**

Search the **Community AMIs** for "Dynatrace DEM Workshop"

![Deploy](/assets/pre-publicami.png)

Click **Select** to start in deployment wizard.

Use the defaults to create the instance except:

* Instance Type: **t2.medium**
	
* Security group: Ensure the security group includes **SSH** and **HTTP** ports


![Deploy](/assets/pre-securitygroup.png)

Create a new key pair or use an existing one. **Please note: you will need the PEM key to access the instance via SSH.**

Launch the instance...

---
:arrow_up_small: [Back to overview](/README.md)
