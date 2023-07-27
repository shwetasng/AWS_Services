## Monitoring Services in AWS
## Creating a CloudWatch Alarm That Initiates an Amazon SNS Message
### Create an Amazon CloudWatch alarm to notify you when the account has spent over a certain amount of money. The alarm sends a message to Amazon Simple Notification Service (Amazon SNS) to send an email or text notification.

### Task 1. Create and subscribe to an SNS topic
1. Choose the **Services** menu, locate the **Application Integration** section, and choose **Simple Notification Service**. <img width="648" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/063dec7a-0963-4b5c-ac86-69686bc5ee62">

2. In the left navigation pane, select **Topics**.
   - **Note:** If you don't see the left navigation pane, choose the hamburger menu  icon.
3. Select **Create topic** <img width="668" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/201c354e-0e9b-4c6c-b5f5-daeb126604d8">

   - A Topic acts as a communication channel where messages from alerts and events can be posted.
4. For **Type**, select **Standard**.
5. For **Name**, enter `MoneyAlert`. <img width="602" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/53a121cc-42a4-486d-8bed-386cdc7f8018">

6. Choose **Create topic**.
   - Now, you will subscribe to that topic so when a message is posted to the topic, it will be pushed to your phone or email.
7. In the **Subscriptions** section, choose **Create subscription**. <img width="653" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/942780d0-d265-4223-a7d7-e4ec367adf4f">

8. For **Topic ARN**, select the **MoneyAlert** topic you created.
9. For **Protocol**, select **Email** to get an email alert.
10. For **Endpoint**, enter your email address or phone number, depending on what you selected for **Protocol**. <img width="599" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/423a1ab9-25cb-4ed1-b062-5d5835d38954">

11. Select **Create subscription**.
    - **Note:** A confirmation message displays at the top of the page. Make sure to **Confirm subscription** once the email is received.
      <img width="559" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b05b2a59-dd87-4c18-8d63-a62c0e891b04">



### Task 2. Create a CloudWatch alarm
- Now you will create the billing alert.
12. Choose the **Services** menu, locate the **Management & Governance** section, and choose **CloudWatch**. <img width="657" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/34cc9ae0-8a89-405b-b54d-fcfb8d7b3803">

13. In the left navigation pane, select **Alarms**.
14. Choose **Create alarm**. <img width="766" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c12525ff-a7c5-4f56-97b8-7cd73999ae70">

15. Choose **Select metric**. <img width="808" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/d1d820bc-7924-4853-ad0c-fc1c09a8c3ca">

16. Select **Billing**. <img width="529" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/15e35172-0153-4f87-8cb4-555b56e47375">

17. Select **Total Estimated Charge**.
18. Check the box for **EstimatedCharges**. <img width="796" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/45637aed-5134-4c31-b849-09a7175eec7e">

19. Choose **Select metric**.
20. In the **Conditions** section, configure the following:
    - For **Threshold type**, select **Static**.
    - For **Whenever EstimatedCharges is…**, select **Greater**.
    - For **than...**, enter `100` into the textbox.
      <img width="611" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a88d9244-1b8b-4ba8-bee6-137fe86e6988">

21. Choose **Next**.
22. In the **Notification** section, configure the following:
    - For **Alarm state trigger**, choose **In alarm**.
    - For **Send a notification to the following SNS topic**, choose **Select an existing SNS topic**.
    - For **Send a notification to...**, choose the **MoneyAlert** topic.
      <img width="599" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/56ce40a7-e97f-49e7-9c3a-fea626ddc6e7">

23. Choose **Next**.
24. For **Alarm name**, enter `MoneyAlertAlarm`. <img width="451" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/35ee9b63-ea56-4c30-8097-1aee76132361">

25. Choose **Next**.
26. Review the settings. Scroll down and choose **Create alarm**.
<img width="773" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/4c63cb01-c311-4624-ac81-7f2e3619973a">

- Congratulations! You have set up a CloudWatch alarm that uses Amazon SNS to send an alert when the cost of services reaches $100.
