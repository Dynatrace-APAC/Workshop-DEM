## Exercise 4
This exercise covers configuring Session Replay in Dynatrace.

Read about Session Replay here: [How to use Dynatrace > Real User Monitoring > Basic RUM concepts > Session Replay](https://www.dynatrace.com/support/help/how-to-use-dynatrace/real-user-monitoring/basic-concepts/session-replay/)

### 1. Enable Session Replay

1. Select Applications from the navigation menu.
2. Select the application you want to configure.
3. Click the Browse \[...\] menu button and select Edit.
4. From the Application settings menu, select Session Replay.
5. Turn the Enable Session Replay button on.

   ![SR](/assets/401-Configure.png)

6. Click on Save and then access Easy Travel on the browser and fire off some transactions.
7. After a couple minutes, find your session under User Sessions
   * Hint: You can filter for sessions that have Replay enabled

   ![SR](/assets/403-ViewSR1.png)

8. Replay your session

![SR](/assets/403-ViewSR2.png)

![SR](/assets/403-ViewSR3.png)

![SR](/assets/403-ViewSR4.png)


### 2. Additional configuration for for personal data protection

Reference: https://www.dynatrace.com/support/help/how-to-use-dynatrace/real-user-monitoring/setup-and-configuration/web-applications/additional-configuration/configure-session-replay-for-personal-data-protection/

![SR](/assets/402-Privacy.png)

---

:arrow_forward: [Next Hands On: User Session Query Language (USQL)](/Hands%20On%205%20-%20Introduction%20to%20USQL)

:arrow_up_small: [Back to overview](https://github.com/performgohot19/DEM)
