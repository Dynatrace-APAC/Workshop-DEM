## Exercise 2
In this exercise, we will cover the basics of configuring Real User Monitoring. These are some of the best practices that should be followed every time the Dynatrace JavaScript agent is deployed, be it an automated or manual injection. 

More information can be found here: [How to use Dynatrace > Real User Monitoring > Setup and configuration > Web applications](https://www.dynatrace.com/support/help/how-to-use-dynatrace/real-user-monitoring/setup-and-configuration/web-applications/)

There are 3 tasks in this exercies:
- [ ] Task1 Defining an application
- [ ] Task2 Selecting the appropriate JavaScript frameworks
- [ ] Task3 Tagging a user session

### Task 1. Defining an application

Reference: https://www.dynatrace.com/support/help/how-to-use-dynatrace/real-user-monitoring/setup-and-configuration/web-applications/initial-configuration/define-your-applications-via-the-my-web-application-placeholder

1. Select Applications from the navigation menu.
2. Click the My web application placeholder application.
3. Scroll down to find the Top 3 included domains panel. This panel includes the domains that contain the largest number of actions that have been automatically detected by OneAgent in your environment.
4. Click View full details.

   ![Deploy](/assets/201-Define.png)

5. Select a domain from the list appearing under Top domains and expand it by clicking the arrow under Transfer domain.
6. Click Create new application. Your application will be created and listed on the Applications page. From now on, all user actions that are monitored on this domain will be mapped onto the newly created application. Alternatively, you may want to add the domain to an existing application, in case some applications have already been created. To do this, expand the list box, select an application and click Transfer.

   ![Deploy](/assets/201-Create.png)

As you may want to use a more intuitive name for your application, you can easily rename it. To rename an application:
1. Select Applications from the navigation menu.
2. Click your newly created application to access the application's overview page.
3. Click the Browse button (...) and select Edit.
4. Type in the name you prefer in the text box appearing on top of the page. Note that application names must be unique.

### Task 2. Selecting the appropriate JavaScript frameworks

1. Select Applications from the navigation menu.
2. Select the newly created application (the entry in your Dynatrace console will be different from the screen shot)

   ![Deploy](/assets/202-ModifyJSFramework.png)

3. Click the Browse button (...) and select Edit.
4. Select "Async request..."
5. Enable the following framewoks as shown in the screen below
6. Click on Save

   ![Deploy](/assets/202-ConfigFramework.png)

### Task 3. Tagging a user session

Reference: https://www.dynatrace.com/support/help/how-to-use-dynatrace/real-user-monitoring/how-to-use-real-user-monitoring/cross-application-user-session-analytics/identify-individual-users-for-session-analysis/

We will be tagging users based on page metadata.

This approach to user tagging works by capturing available data in your application’s page source. If you take a close look at your application’s page source, you’ll likely find that usernames are already included somewhere. Usernames may be included in the text of a DOM element, a meta tag, a JavaScript variable, or even a cookie attribute. For example, easyTravel, the Dynatrace demo application, includes the user name in a welcome message in the upper-right corner of the home page (see image below). Using the development tools that are built into most browsers, you can generate a unique CSS selector for this particular element.

![User tagging based on page metadata](https://dt-cdn.net/images/usertags2-1872-eaa3cbf0fe.png)

Once you’ve identified where usernames are located in your page source, you can create user tags based on the usernames. To do this, return to Dynatrace and execute the following steps:

1. Select "User tag"
2. Click on "Add tag (identifier) rule"
3. Select the drop down "CSS Selector"
4. Paste the CSS Selector which you copied earlier from your browser's Developer Tool. Since the CSS Selector also picks up some additional text, we can apply a clean up rule.
5. Click on Save

   ![Deploy](/assets/204-TaggingUserSession.png)

**Hint:**
 * CSS Selector
 
   ```#loginForm\:j_idt39```
 
 * Clean up rule
 
    ```Hello (.*)!```

---

:arrow_forward: [Next Hands On: Configure Synthetic in Dynatrace](/Hands%20On%203%20-%20Configure%20Synthetic%20Test)

:arrow_up_small: [Back to overview](/README.md)
