## Hands On 1 : Deploy Dynatrace OneAgent
In this exercise, we will deploy the OneAgent to a Linux instance and let the OneAgent discover what is running in that instance.

### 1. Download the OneAgent

Use PuTTy (Windows) or Terminal (Mac), ssh into the instance (IP address, userid and password will be provided to you)

```bash
login as: perform
perform@1.1.1.1's password:

```

Open your browser and access the Dynatrace URL.

Select Deploy Dynatrace from the navigation menu.

![Deploy](/assets/101-DeployDynatrace.jpg)

Click the Start installation button and select Linux.

![Deploy](/assets/102-StartInstallation.jpg)

![Deploy](/assets/103-Linux.jpg)


Choose the installer type from the drop-down list. Use the Linux shell script installer on any Linux system that's supported by Dynatrace, regardless of the packaging system your distribution depends on.

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

**Note that you’ll need root access.**  You can use su or sudo to run the installation script. To do this, type one of the following commands into the directory where you downloaded the installation script.

Example:

```bash
$ sudo /bin/sh Dynatrace-OneAgent-Linux-1.171.252.sh
[sudo] password for perform:
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

Execute the command

```
$ cd ~
$ ./starteasytravel.sh
...
--> Deploying template "easytravel/easytravel-with-loadgen" for "easytravel-with-loadgen.yml" to project easytravel

     easytravel-with-loadgen
     ---------
     The Dynatrace easyTravel sample application (with UEM loadgen).

--> Creating resources ...
    deploymentconfig.apps.openshift.io "mongodb" created
    deploymentconfig.apps.openshift.io "backend" created
    deploymentconfig.apps.openshift.io "frontend" created
    deploymentconfig.apps.openshift.io "www" created
    deploymentconfig.apps.openshift.io "loadgen" created
    service "mongodb" created
    service "backend" created
    service "frontend" created
    service "www" created
    route.route.openshift.io "www" created
--> Success
    Access your application via route 'www-easytravel.<your public ip>.nip.io'
    Run 'oc status' to view your app.

```

Easy Travel will take about 5 minutes to complete starting up. If you would like to check the status, you can enter this command

```bash
$ oc status | grep nginx -A 1 | grep "\- 1 pod"
    deployment #1 deployed 7 minutes ago - 1 pod (warning: 3 restarts)
```

If you see the above message, it would mean that the frontend web server is ready. If you do not see anything, it means that Easy Travel is still starting and you might want to wait a few minutes more. 

To access the Easy Travel portal, copy the URL shown to you:

![Deploy](/assets/107-EasyTravelURL.jpg)

If you need the URL again, execute the command

```bash
$ cd ~
$ ./showurl.sh
Easytravel URL: www-easytravel.<your public ip>.nip.io
```

### 5. Explore the Smartscape

While waiting for Easy Travel to start, you can explore Dynatrace and using the Smartscape, Dynatrace will automatically discover the processes and dependencies that comprises the Easy Travel application! 

[4 things](https://www.dynatrace.com/support/help/get-started/4-things-youll-absolutely-love-about-dynatrace/) that you will love about Dynatrace!

![Smartscape](https://dt-cdn.net/images/smartscape-horizontal-topology-2-860-6bdf46eb74.png)

---

:arrow_forward: [Next Hands On: Configure Real User Monitoring in Dynatrace](/Hands%20On%202%20-%20Configure%20Real%20User%20Monitoring)

:arrow_up_small: [Back to overview](/README.md)
