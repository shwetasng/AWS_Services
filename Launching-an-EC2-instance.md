# Module 4 Lab 1: Launching an EC2 Instance
## Lab overview
In this lab, you create an Amazon Elastic Compute Cloud (Amazon EC2) instance that hosts a simple website.

 

## Duration
This lab requires approximately 30 minutes to complete.

 

## Access the AWS Management Console
1. To start the lab session, choose  Start Lab in the upper-right corner of the page.
   - The lab session starts.
   - A timer displays in the upper-right corner of the page and shows the time remaining in the session.

     Tip: To refresh the session length at any time, choose Start Lab again before the timer reaches 0:00.

     Before continuing, wait until the lab environment is ready. The environment is ready when the lab details appear on the right side of the page and the circle icon next to the AWS link in the upper-left corner turns green.

 

2. To return to these instructions, choose the  Readme link in the upper-right corner.

 

3. To connect to the AWS Management Console, choose the AWS link in the upper-left corner, above the terminal window.

A new browser tab opens and connects you to the AWS Management Console.

Tip: If a new browser tab does not open, a banner or icon is usually at the top of your browser with the message that your browser is preventing the site from opening pop-up windows. Choose the banner or icon, and then choose Allow pop-ups.

 

## Task 1. Start creating the instance and assign a name
4. Choose the Services menu, locate the Compute services, and select EC2.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/8b0cb013-9937-43ff-8a97-b1250efbd49a">


 

5. Choose the Launch instance button in the middle of the page, and then select Launch instance from the dropdown menu.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/21f3d743-f7e2-431b-b10a-4e876e8fd2cf">

 

6. Name the instance:

Give it the name Web Server 1
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f15c3efa-4d92-4d50-bf2c-f389b362650b">

Tags help you categorize your AWS resources in different ways; for example, by purpose, owner, or environment. This is useful when you have many resources of the same type—you can quickly identify a specific resource based on the tags you have assigned to it. Each tag consists of a key and a value, which you define. 

Note: Name is simply another tag. The key for this tag is Name, and the value is Web Server 1.

 

## Task 2. Application and OS Images
7. Choose an AMI from which to create the instance:
   - In the list of available Quick Start AMIs, keep the default Amazon Linux AMI selected. 
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ab0c4b52-eada-4fc6-9cb2-27502fec060f">

   - Also keep the default Amazon Linux 2023 AMI x86_64 (HVM) selected.

The type of Amazon Machine Image (AMI) you choose determines the Operating System (OS) that will run on the EC2 instance that you launch. In this case, you have chosen Amazon Linux 2023 as the guest OS.

 

## Task 3. Choose an instance type
8. Specify an Instance type:

 - In the Instance type panel, keep the default t2.micro selected.
<img width="571" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/62aa190e-3068-42a2-bfc6-39c24e19ef39">


The Instance Type defines the hardware resources assigned to the instance. This instance type has 1 virtual central processing unit (CPU) and 1 GiB of memory.

 

## Task 4. Choose a key pair
9. Select the key pair to associate with the instance:

 - From the Key pair name menu, select vockey.
<img width="560" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/705926c8-1336-4be3-a682-f461901f5c89">


The vockey key pair you selected will allow you to connect to this instance via SSH after it has launched. Although you will not need to do that in this lab, it is still required to identify an existing key pair, or create a new one, when you launch an instance.

 

## Task 5. Network settings
10. Next to Network settings, choose Edit.

 

11. Keep the default VPC and subnet settings. Also keep the Auto-assign public IP setting set to Enable.
<img width="565" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b068b125-af07-4af2-9149-3618a1df673b">


 The Network indicates the virtual private cloud (VPC) you want to launch the instance into. You can have multiple networks; for example, one for development, a second for testing, and a third for production.

 

12. Under Firewall (security groups), keep the default  Create security group option chosen.

 

13. Configure a new security group:

    - Keep the default selection Create a new security group.
     
    - Security group name: Clear the text and enter Web Server 
     
    - Description: Clear the text and enter Security group for my web server
     
    - Choose Remove to remove the default SSH inbound rule. 
     <img width="545" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/0e96e3a5-d38e-41c6-b5a1-f72d613abfd1">


Note: You will configure a different inbound rule later in this lab.

A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time. The new rules are automatically applied to all instances that are associated with the security group.

 

## Task 6. Configure storage
14. In the Configure storage section, keep the default settings.
<img width="551" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/24e6ffd8-9113-4b5d-a846-bc9a229deb5c">


You will launch the Amazon EC2 instance using a default Elastic Block Store (EBS) disk volume. This will be your root volume (also known as a boot volume) which will host the Amazon Linux 2023 guest operating system that you specified earlier. It will run on a general purpose SSD (gp2) hard drive that is 8 GiB in size. You could alternatively add more storage volumes, however that is not needed in this lab.

 

## Task 7. Advanced details
15. Configure a script to run on the instance when it launches: 

   - Expand the Advanced details panel.

   - Scroll to the bottom of the page and then copy and paste the code shown below into the User data box:
<img width="440" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/d2f47638-7930-4e13-b224-798b5f7f8b8b">

  ```text
  #!/bin/bash
  yum update -y
  yum -y install httpd
  systemctl enable httpd
  systemctl start httpd
  echo '<html><h1>Hello World!</h1></html>' > /var/www/html/index.html
  ```
This bash script will run with root user permissions on the guest OS of the instance. It will run automatically when the instance launches for the first time. This script does the following:

- Updates the server
- Installs an Apache web server (httpd)
- Configures the web server to automatically start on boot
- Activates the web server
- Creates a simple webpage
 

## Task 8. Review the instance and launch
16. At the bottom of the Summary panel on the right side of the screen choose Launch instance

You will see a Success message.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/84ea5c07-0f1e-4cda-bd1f-f0ce410fde9a">


 

17. Choose View all instances

The instance will first appear in the Pending state, which means it is being launched. The state will then change to Running, which indicates that the instance has started booting. It takes a few minutes for the instance to boot.
<img width="770" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/7c565bbb-5e6b-4ee2-bb16-3d24f3fd766f">

 

18. Select the Web Server 1 instance, and review the information in the Details tab that displays in the lower pane.

Notice that the instance has a Public IPv4 address. You can use this IP address to communicate with the instance from the internet.
<img width="782" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f0287bb1-3904-4d86-801e-120949381209">

 

19. Before you continue, wait for your instance to display the following:

 - Instance state: Running

 - Status check: 2/2 checks passed

 :left_speech_bubble:This may take a few minutes. Choose the refresh icon at the top of the page every 30 seconds or so to more quickly become aware of the latest status of the instance.

 

## Task 9. Access your EC2 instance
When you launched your EC2 instance, you provided a script that installed a web server and created a simple webpage. In this task, you will try to access the content from the web server.

 

20. From the Details tab, copy the Public IPv4 address value of your instance to your clipboard.

Note: A public address means that the instance can be reached from the internet. Each instance that receives a public IP address is also given an external DNS hostname; for example, ec2-xxx-xxx-xxx-xxx.compute-1.amazonaws.com. AWS resolves an external DNS hostname to the public IP address of the instance when communication comes from outside its VPC. When communication comes from inside its VPC, the DNS hostname is resolved to the private IPv4 address.

 

21. Open a new tab in your web browser, paste the public IP address you just copied, and press Enter.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/99761fab-fbbb-4d4f-a7ad-bc75358b1918">


The webpage does not load. You must update the security group to be able to access the page.

 

## Task 10. Update the security group
You are not able to access your web server because the security group is not permitting inbound traffic on port 80, which is used for HTTP web requests. In this task, you update the security group.

 

22. Return to the EC2 Management Console browser tab.

 

23. In the left navigation pane, under Network & Security, choose Security Groups.
<img width="171" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/82ad8326-494d-4f48-807a-845356232281">

 

24. Select the Web Server security group, which you created when launching your EC2 instance.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/33ef328e-b99a-4da3-adf0-da684ff9d3f7">

 

25.In the lower pane, choose the Inbound rules tab.
<img width="717" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/0733c91e-af28-448f-90a2-8b557141763f">

 

## Task 11. Create an inbound rule
26. Choose Edit inbound rules, and then choose Add rule.
<img width="706" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/65770b44-2ddf-431d-9ffd-ca86e44f0172">

 

27. Configure the following:

  - Type: HTTP
  - Source: Anywhere-IPv4
  - Choose Save rules
  <img width="909" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/1c3f242e-ba20-4ca9-aeff-cba295c5cdeb">

The new inbound HTTP rule creates an entry for IPv4 IP (0.0.0.0/0) and IPv6 IP addresses (::/0).

 

## Task 12. Test the rule
28. Return to the tab that you used to try to connect to the web server.

 

29. Refresh the page.

The page should display the message Hello World!
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b5a3905c-b6d2-4863-a2c8-ea80f10a6d63">

 

## Lab complete
Congratulations! You have completed the lab.

 

30. Log out of the AWS Management Console.

  - In the upper-right corner of the page, choose your user name. Your user name begins with voclabs/user.
  
  - Choose Sign out.

 

31. Choose End Lab at the top of this page, and then select Yes to confirm that you want to end the lab.
