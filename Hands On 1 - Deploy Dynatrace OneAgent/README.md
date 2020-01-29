## Hands On 1 : Deploy Dynatrace OneAgent
In this exercise, we will deploy the OneAgent to a Linux instance and let the OneAgent discover what is running in that instance.

### 1. Download the OneAgent

Use PuTTy (Windows) or Terminal (Mac), ssh into the instance (IP address using the your PEM Key)

Open your browser and access the Dynatrace URL.

Select Deploy Dynatrace from the navigation menu.

![Deploy](/assets/101-DeployDynatrace.jpg)

Click the Start installation button and select Linux.

![Deploy](/assets/102-StartInstallation.jpg)

![Deploy](/assets/103-Linux.jpg)


Choose the installer type from the drop-down list (we'll use the default x86/64). 
Use the Linux shell script installer on any Linux system that's supported by Dynatrace, regardless of the packaging system your distribution depends on.

**Copy** the command provided in the "Use this command on the target host" text field. **Paste** the command into your terminal window and execute it.

![Deploy](/assets/104-Download.jpg)

Example: 

```bash
$  wget  -O Dynatrace-OneAgent-Linux-1.171.252.sh <follow screen shot above>
--2019-08-07 10:17:45--  https://<URL>
Resolving <URL>... <IP>
Connecting to <URL> | <IP>|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139134801 (133M) [application/octet-stream]
Saving to: ‘Dynatrace-OneAgent-Linux-1.171.252.sh’

100%[======================================>] 139,134,801 84.3MB/s   in 1.6s

2019-08-07 10:17:47 (84.3 MB/s) - ‘Dynatrace-OneAgent-Linux-1.171.252.sh’ saved [139134801/139134801]

$
```

### 2. Execute the installation script

(Optional) Once the download is complete, you can verify the signature by copying the command from the "Verify signature" text field, then pasting the command into your terminal window and executing it. Make sure your system is up to date, especially SSL and related certificate libraries.

**Copy** the command that's provided in the text box "And run the installer with root rights" text field.

![Deploy](/assets/105-Install.jpg)

**Paste** the command into your terminal window and execute it. You’ll need to make the script executable before you can run it.

**Note that you’ll need root access.**  You can use sudo to run the installation script. To do this, type the following command into the directory where you downloaded the installation script.

Example:

```bash
$ sudo /bin/sh Dynatrace-OneAgent-Linux-1.171.252.sh
10:21:42 Checking root privileges...
10:21:42 OK
10:21:42 Installation started ...
...
10:22:14 Starting agents...
10:22:14 oneagent service started
10:22:14 Checking if agent is connected to the server...
10:22:16 Dynatrace OneAgent has successfully connected to Dynatrace Cluster Node. After completing Dynatrace OneAgent installation on this machine, please return to your browser to complete the remainder of the installation.
$

```

### 3. Validate the installation in Deployment status

![Deploy](/assets/106-Status.jpg)

Reference: https://www.dynatrace.com/support/help/technology-support/operating-systems/linux/

### 4. Start Easy Travel application

To start Easy Travel execute the following command:

```
$ cd ~
$ ./restart_easyTravel.sh
Stopping loadgen  ... done
Stopping www      ... done
Stopping frontend ... done
Stopping backend  ... done
Stopping mongodb  ... done
Removing loadgen  ... done
Removing www      ... done
Removing frontend ... done
Removing backend  ... done
Removing mongodb  ... done
ip-172-31-7-147
APM
Creating mongodb ... done
Creating backend ... done
Creating frontend ... done
Creating www      ... done
Creating loadgen  ... done
$

```

Easy Travel will take about 5 minutes to complete starting up. If you would like to check the status, you can enter this command:

```bash
$ sudo docker ps
CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS              PORTS                                                NAMES
0f9cb477bcf0        dynatrace/easytravel-loadgen    "/bin/sh -c /run-pro…"   19 minutes ago      Up 19 minutes                                                            loadgen
a3d241d88ecf        dynatrace/easytravel-nginx      "/bin/sh -c /run-pro…"   19 minutes ago      Up 19 minutes       443/tcp, 0.0.0.0:80->80/tcp, 8080/tcp                www
82300947a19a        dynatrace/easytravel-frontend   "/bin/sh -c /run-pro…"   19 minutes ago      Up 19 minutes       0.0.0.0:32771->8080/tcp                              frontend
3dc6e8e3f468        dynatrace/easytravel-backend    "/bin/sh -c /run-pro…"   19 minutes ago      Up 19 minutes       0.0.0.0:32770->8080/tcp                              backend
f88098f89e90        dynatrace/easytravel-mongodb    "/bin/sh -c ${SCRIPT…"   19 minutes ago      Up 19 minutes       0.0.0.0:32769->27017/tcp, 0.0.0.0:32768->28017/tcp   mongodb

```

If you see the above 5 containers, it would mean that Easy Travel containers have started. If you do not see the 5 conatiners, it means that Easy Travel is still starting and you might want to wait a few minutes more. 

To access the Easy Travel portal, use the Public DNS of your instance. Copy / paste the Public DNS into your browser.

Get the Public DNS for your instance from the AWS Console or execute this command:

```bash
$ curl http://169.254.169.254/latest/meta-data/public-hostname
ec2-xxx-xxx-xxx-xxx.ap-southeast-2.compute.amazonaws.com
```

### 5. Explore the Smartscape

While waiting for Easy Travel to start, you can explore Dynatrace and using the Smartscape, Dynatrace will automatically discover the processes and dependencies that comprises the Easy Travel application! 

[4 things](https://www.dynatrace.com/support/help/get-started/4-things-youll-absolutely-love-about-dynatrace/) that you will love about Dynatrace!

![Smartscape](https://dt-cdn.net/images/smartscape-horizontal-topology-2-860-6bdf46eb74.png)

---

:arrow_forward: [Next Hands On: Configure Real User Monitoring in Dynatrace](/Hands%20On%202%20-%20Configure%20Real%20User%20Monitoring)

:arrow_up_small: [Back to overview](/README.md)
