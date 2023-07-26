## AWS Elastic Block Storage
- In this practical, you will create an Amazon Elastic Compute Cloud (Amazon EC2) instance and then attach an Amazon Elastic Block Store (Amazon EBS) volume to it.

### Task 1. Start creating the instance and assign a name
1. Choose the **Services** menu, locate the **Compute** services, and select **EC2**.
<img width="713" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c23db25c-2e0a-47fc-b30e-ebda34951e6f">

2. Choose the **Launch instance** button in the middle of the page, and then select **Launch instance** from the dropdown menu. 
<img width="765" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f235c347-ef84-49d5-b474-aa368186b571">

3. Name the instance:
   - Give it the name `Web Server`
   <img width="560" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a0dc5a68-49bc-4fd6-a1a6-0cce2763bce1">

   - Tags help you categorize your AWS resources in different ways; for example, by purpose, owner, or environment. This is useful when you have many resources of the same type—you can quickly identify a specific resource based on the tags you have assigned to it. Each tag consists of a key and a value, which you define.
   - **NOTE:** *Name* is simply another tag. The key for this tag is `Name`, and the value is `Web Server 1`.


### Task 2. Application and OS Images
4. Choose an AMI from which to create the instance:
   - In the list of available Quick Start AMIs, keep the default **Amazon Linux** AMI selected.
   - Also keep the default **Amazon Linux 2023 AMI x86_64 (HVM)** selected.
   - The type of *Amazon Machine Image (AMI)* you choose determines the Operating System (OS) that will run on the EC2 instance that you launch. In the case, you have chosen Amazon Linux 2023 as the guest OS.
<img width="538" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b756cf1f-da6c-45bf-b362-df9b84eafa19">


### Task 3. Choose an instance type
5. Specify an Instance type:
   - In the *Instance type* panel, keep the default **t2.micro** selected.
   - The *Instance Type* defines the hardware resources assigned to the instance. This instance type has 1 virtual central processing unit (CPU) and 1 GiB of memory
   <img width="558" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b8cdd536-17f1-45ce-a066-62446b282af8">


### Task 4. Choose a key pair
6. Select the key pair to associate with the instance:
   - From the **Key pair name** menu, select **vockey**.
   - The *vockey key pair* you selected will allow you to connect to this instance via SSH after it has launched.
     <img width="547" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/51f81f2f-d4b9-43c6-a6c3-0d40d9267159">



### Task 5. Network settings
7. Next to Network settings, choose **Edit**.
8. Keep the default VPC and subnet settings. Also keep the **Auto-assign public IP** setting set to **Enable**. <img width="531" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ea92196a-5420-4bf1-80c2-d6bd8de12b41">

   - The Network indicates the virtual private cloud (VPC) you want to launch the instance into. You can have multiple networks; for example, one for *development*, a second for *testing*, and a third for *production*.
9. Under Firewall (security groups), keep the default  **Create security group** option chosen.
10. Configure a new security group:
    - Keep the default selection **Create a new security group**.
    - **Security group name:** Clear the text and enter `Web Server`
    - **Description:** Clear the text and enter `Security group for my web server`
    - Choose **Remove** to remove the default SSH inbound rule.
    <img width="522" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/bd42574c-6185-4bfb-9a4a-dae99923f3f5">

    - ***Note:*** You will configure a different inbound rule later in this lab.
    - A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time. The new rules are automatically applied to all instances that are associated with the security group.


### Task 6. Configure storage
11. In the *Configure storage* section, keep the default settings.
    - You will launch the Amazon EC2 instance using a default Elastic Block Store (EBS) disk volume. This will be your root volume (also known as a boot volume) which will host the Amazon Linux 2023 guest operating system that you specified earlier. It will run on a general purpose SSD (gp2) hard drive that is 8 GiB in size. You could alternatively add more storage volumes, however that is not needed in this lab.
<img width="542" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a948a69d-83fa-4b69-92e8-3063efb58db3">


### Task 7. Advanced details
12. Configure a script to run on the instance when it launches:
    - Expand the **Advanced details** panel.
    - Scroll to the bottom of the page and then copy and paste the code shown below into the **User data** box:
    ```text
    #!/bin/bash
    yum update -y
    yum -y install httpd
    systemctl enable httpd
    systemctl start httpd
    echo '<html><h1>Hello World!</h1></html>' > /var/www/html/index.html
    ```
    <img width="399" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/58033892-576d-42ad-8c95-51c7358cc4bf">

    This bash script will run with root user permissions on the guest OS of the instance. It will run automatically when the instance launches for the first time. This script does the following:
    - Updates the server
    - Installs an Apache web server (httpd)
    - Configures the web server to automatically start on boot
    - Activates the web server
    - Creates a simple webpage
### Task 8. Review the instance and launch
13. At the bottom of the **Summary** panel on the right side of the screen choose **`Launch instance`**
    - You will see a Success message.
    <img width="857" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/0ea5620b-89a7-4e70-8b5d-687779491be5">

14. Choose **`View all instances`**
    - The instance will first appear in the *Pending state*, which means it is being launched. The state will then change to *Running*, which indicates that the instance has started booting. It takes a few minutes for the instance to boot.
15. Select the **Web Server** instance, and review the information in the **Details** tab that displays in the lower pane.
    - Notice that the instance has a **Public IPv4 address**. You can use this IP address to communicate with the instance from the internet.
16. Before you continue, wait for your instance to display the following:
    - **Instance state:** *Running*
    - **Status check:** *2/2 checks passed*
    ***NOTE:*** This may take a few minutes. Choose the refresh  icon at the top of the page every 30 seconds or so to more quickly become aware of the latest status of the instance.
      <img width="763" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/0f7c4f04-5465-49d2-ab28-b9866ed7d1f7">

### Task 9. Access your EC2 instance
- When you launched your EC2 instance, you provided a script that installed a web server and created a simple webpage. In this task, you will try to access the content from the web server.
17. From the **Details** tab, copy the **Public IPv4 address** value of your instance to your clipboard.
***NOTE:*** Note: A public address means that the instance can be reached from the internet. Each instance that receives a public IP address is also given an external DNS hostname; for example, ec2-xxx-xxx-xxx-xxx.compute-1.amazonaws.com. AWS resolves an external DNS hostname to the public IP address of the instance when communicate comes from outside its VPC. When communicate comes from inside its VPC, the DNS hostname is resolved to the private IPv4 address.
  <img width="627" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/00ee8ade-3b30-4f55-a3ee-7ee0a9071538">

18. Open a new tab in your web browser, paste the public IP address you just copied, and press **Enter**.
    - The webpage does not load. You must update the security group to be able to access the page.
    <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/8eab8405-75c4-41d6-8558-2f8aa7ccd2e5">

### Task 10. Update the security group
- You are not able to access your web server because the security group is not permitting inbound traffic on port 80, which is used for HTTP web requests. In this task, you update the security group.
19. Return to the **EC2 Management Console** browser tab.
20. In the left navigation pane, under **Network & Security**, choose **Security Groups**.
21. Select the **Web Server** security group, which you created when launching your EC2 instance. <img width="735" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/14d86cd6-9b6d-4f86-baaf-01acfc321387">

22. In the lower pane, choose the **Inbound rules** tab
### Task 11. Create an inbound rule
23. Choose **Edit inbound rules**, and then choose **Add rule**. <img width="708" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/658ce9ea-134b-4216-9731-019c19d300a0">

24. Configure the following:
    - **Type:** HTTP
    - **Source:** Anywhere-IPv4
    - Choose **Save rules**
      <img width="890" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/6e79cd4c-4532-4f86-a458-26c7d00cd5db">

    The new inbound HTTP rule creates an entry for IPv4 IP (0.0.0.0/0) and IPv6 IP addresses (::/0).
### Task 12. Test the rule
25. Return to the tab that you used to try to connect to the web server.
26. Refresh the page.
    The page should display the message *Hello World!*
    <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a9ef85e1-4c12-4611-a435-1f9bb33e3387">

### Task 13. Attach an EBS volume to your EC2 instance
27. Return to the **EC2 Management Console** browser tab.
28. In the left navigation pane, under **Instances**, choose **Instances**.
29. Select the **Web Server** instance, and in the **Networking** tab below, note the **Availability Zone** in which your instance is running. 
<img width="196" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/7f5638dc-9ad2-41be-92b2-a65eb06b627c">

- The EBS volume you will soon create will need to be in the same Availability Zone.
30. In the left navigation pane, under **Elastic Block Store**, select **Volumes**. 
<img width="161" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/587f6ff1-c7b6-4fc9-827a-00aca9026ba7">

31. Select **Create volume**.
32. For **Size**, enter `1` to create a volume with 1 GiB.
33. For **Availability Zone**, select the same Availability Zone that your EC2 instance is running in. 
<img width="367" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f4a15898-fccb-4f7a-b5f6-12fc9870ab74">

34. Scroll down and select **Create volume**.
    - The new volume appears in the volumes list with a state of *available*.
35. Select the new 1 GiB size volume. Then, choose **Actions**, and **Attach volume**. 
<img width="737" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/2f079493-74d3-489f-a983-b3d12b7187cc">

36. Select the **Instance** drop-down menu, and then select your EC2 instance. The list of instances will automatically populate. 
<img width="481" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/8bbbbaf4-3daf-405e-91c4-4654e46402fa">

37. Select **Attach volume**.
    - The state of the volume changes to *in-use*. The new volume is now attached to your EC2 instance.
      <img width="740" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/04c01b2e-e822-43c0-94a3-0d1ee205a1b4">

### LAB COMPLETE
Congratulations! you have completed the lab.

