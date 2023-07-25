Module 4 Lab 1: Launching an EC2 Instance
Lab overview
In this lab, you create an Amazon Elastic Compute Cloud (Amazon EC2) instance that hosts a simple website.

 

Duration
This lab requires approximately 30 minutes to complete.

 

Access the AWS Management Console
To start the lab session, choose  Start Lab in the upper-right corner of the page.

The lab session starts.

A timer displays in the upper-right corner of the page and shows the time remaining in the session.

Tip: To refresh the session length at any time, choose Start Lab again before the timer reaches 0:00.

Before continuing, wait until the lab environment is ready. The environment is ready when the lab details appear on the right side of the page and the circle icon next to the AWS link in the upper-left corner turns green.

 

To return to these instructions, choose the  Readme link in the upper-right corner.

 

To connect to the AWS Management Console, choose the AWS link in the upper-left corner, above the terminal window.

A new browser tab opens and connects you to the AWS Management Console.

Tip: If a new browser tab does not open, a banner or icon is usually at the top of your browser with the message that your browser is preventing the site from opening pop-up windows. Choose the banner or icon, and then choose Allow pop-ups.

 

Task 1. Start creating the instance and assign a name
Choose the Services menu, locate the Compute services, and select EC2.

 

Choose the Launch instance button in the middle of the page, and then select Launch instance from the dropdown menu.

 

Name the instance:

Give it the name Web Server 1
Tags help you categorize your AWS resources in different ways; for example, by purpose, owner, or environment. This is useful when you have many resources of the same type—you can quickly identify a specific resource based on the tags you have assigned to it. Each tag consists of a key and a value, which you define. 

Note: Name is simply another tag. The key for this tag is Name, and the value is Web Server 1.

 

Task 2. Application and OS Images
Choose an AMI from which to create the instance:

In the list of available Quick Start AMIs, keep the default Amazon Linux AMI selected. 

Also keep the default Amazon Linux 2023 AMI x86_64 (HVM) selected.

The type of Amazon Machine Image (AMI) you choose determines the Operating System (OS) that will run on the EC2 instance that you launch. In this case, you have chosen Amazon Linux 2023 as the guest OS.

 

Task 3. Choose an instance type
Specify an Instance type:

In the Instance type panel, keep the default t2.micro selected.

The Instance Type defines the hardware resources assigned to the instance. This instance type has 1 virtual central processing unit (CPU) and 1 GiB of memory.

 

Task 4. Choose a key pair
Select the key pair to associate with the instance:

From the Key pair name menu, select vockey.

The vockey key pair you selected will allow you to connect to this instance via SSH after it has launched. Although you will not need to do that in this lab, it is still required to identify an existing key pair, or create a new one, when you launch an instance.

 

Task 5. Network settings
Next to Network settings, choose Edit.

 

Keep the default VPC and subnet settings. Also keep the Auto-assign public IP setting set to Enable.

The Network indicates the virtual private cloud (VPC) you want to launch the instance into. You can have multiple networks; for example, one for development, a second for testing, and a third for production.

 

Under Firewall (security groups), keep the default  Create security group option chosen.

 

Configure a new security group:

Keep the default selection Create a new security group.

Security group name: Clear the text and enter Web Server 

Description: Clear the text and enter Security group for my web server

Choose Remove to remove the default SSH inbound rule. 

Note: You will configure a different inbound rule later in this lab.

A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time. The new rules are automatically applied to all instances that are associated with the security group.

 

Task 6. Configure storage
In the Configure storage section, keep the default settings.

You will launch the Amazon EC2 instance using a default Elastic Block Store (EBS) disk volume. This will be your root volume (also known as a boot volume) which will host the Amazon Linux 2023 guest operating system that you specified earlier. It will run on a general purpose SSD (gp2) hard drive that is 8 GiB in size. You could alternatively add more storage volumes, however that is not needed in this lab.

 

Task 7. Advanced details
Configure a script to run on the instance when it launches: 

Expand the Advanced details panel.

Scroll to the bottom of the page and then copy and paste the code shown below into the User data box:

#!/bin/bash
yum update -y
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello World!</h1></html>' > /var/www/html/index.html
This bash script will run with root user permissions on the guest OS of the instance. It will run automatically when the instance launches for the first time. This script does the following:

Updates the server
Installs an Apache web server (httpd)
Configures the web server to automatically start on boot
Activates the web server
Creates a simple webpage
 

Task 8. Review the instance and launch
At the bottom of the Summary panel on the right side of the screen choose Launch instance

You will see a Success message.

 

Choose View all instances

The instance will first appear in the Pending state, which means it is being launched. The state will then change to Running, which indicates that the instance has started booting. It takes a few minutes for the instance to boot.

 

Select the Web Server 1 instance, and review the information in the Details tab that displays in the lower pane.

Notice that the instance has a Public IPv4 address. You can use this IP address to communicate with the instance from the internet.

 

Before you continue, wait for your instance to display the following:

Instance state: Running

Status check: 2/2 checks passed

 This may take a few minutes. Choose the refresh  icon at the top of the page every 30 seconds or so to more quickly become aware of the latest status of the instance.

 

Task 9. Access your EC2 instance
When you launched your EC2 instance, you provided a script that installed a web server and created a simple webpage. In this task, you will try to access the content from the web server.

 

From the Details tab, copy the Public IPv4 address value of your instance to your clipboard.

Note: A public address means that the instance can be reached from the internet. Each instance that receives a public IP address is also given an external DNS hostname; for example, ec2-xxx-xxx-xxx-xxx.compute-1.amazonaws.com. AWS resolves an external DNS hostname to the public IP address of the instance when communication comes from outside its VPC. When communication comes from inside its VPC, the DNS hostname is resolved to the private IPv4 address.

 

Open a new tab in your web browser, paste the public IP address you just copied, and press Enter.

The webpage does not load. You must update the security group to be able to access the page.

 

Task 10. Update the security group
You are not able to access your web server because the security group is not permitting inbound traffic on port 80, which is used for HTTP web requests. In this task, you update the security group.

 

Return to the EC2 Management Console browser tab.

 

In the left navigation pane, under Network & Security, choose Security Groups.

 

Select the Web Server security group, which you created when launching your EC2 instance.

 

In the lower pane, choose the Inbound rules tab.

 

Task 11. Create an inbound rule
Choose Edit inbound rules, and then choose Add rule.

 

Configure the following:

Type: HTTP
Source: Anywhere-IPv4
Choose Save rules
The new inbound HTTP rule creates an entry for IPv4 IP (0.0.0.0/0) and IPv6 IP addresses (::/0).

 

Task 12. Test the rule
Return to the tab that you used to try to connect to the web server.

 

Refresh the page.

The page should display the message Hello World!

 

Lab complete
Congratulations! You have completed the lab.

 

Log out of the AWS Management Console.

In the upper-right corner of the page, choose your user name. Your user name begins with voclabs/user.

Choose Sign out.

 

Choose End Lab at the top of this page, and then select Yes to confirm that you want to end the lab.
