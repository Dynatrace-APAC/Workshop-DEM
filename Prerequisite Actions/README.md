# Prerequisites Actions for the Dynatrace DEM Workshop 

The following conatins the instructions to create the easyTravel application which will be used duing the DEM workshop.

Access your AWS console and navigate to the **EC2** service.

Select **Instances** > **Launch Instance**

Search the **Community AMIs** for "Dynatrace DEM Workshop"

![Deploy](/assets/pre-publicami.png)

Click **Select** to start in deployment wizard.

Use the defaults to create the instance except:

	Instance Type: **t2.medium** (although t2.micro should work for this session)
	
	Security group: Ensure the security group includes **SSH** and **HTTP** ports

![Deploy](/assets/pre-securitygroup.png)

Create a new key pair or use an existing one. **Please note: you will need the PEM key to access the instance vis SSH.**

Launch the instance...

---
:arrow_up_small: [Back to overview](/README.md)