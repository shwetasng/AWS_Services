## Using Elastic Beanstalk and CloudFormation

### Task 1. Deploy an application using Elastic Beanstalk
1. Choose the **Services** menu, locate the **Compute** services, and choose **Elastic Beanstalk**.

2. Choose **Create Application**.
<img width="802" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ad13e0fe-c784-4424-81c8-b6fac1ea506d">

3. For **Application name**, enter a name for your application; for example, `MyLabApp`
<img width="445" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f5bc7fde-0871-449e-991c-8b64e7628142">

4. For **Platform**, select **PHP**.
<img width="444" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/2a607fab-8345-4bf1-87c5-3167e3febc3d">

5. For **Application code**, select **Sample application**.
<img width="344" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/13af475c-120a-4fe2-bba0-8eea62eb637b">

6. Choose **Next**.

7. Under **Existing service roles** choose the drop-down and select **EMR_EC2_DefaultRole**.

8. Under **EC2 key pair** choose the drop-down and select **vockey**.

9. Under **EC2 instance profile** choose the drop-down and select **EMR_EC2_DefaultRole**.
<img width="581" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/84085d29-8cbd-45eb-9535-f70932f0f4fc">

10. Choose **Next**.

11. Under **VPC** select the available VPC.

12. Under **Public IP address** select **Activated**.

13. Under **Instance subnets** select at least two.
<img width="542" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/81d1890c-4e2d-4f40-9e5a-74b827a98d4e">

14. Choose **Next**.

15. Under EC2 Security groups select the default.

16. Choose Next.

17. Under **Health reporting** choose **Basic**.

18. Under **Managed updates** de-select **Activated**.

19. Choose **Next**.

20. Choose **Submit**.

Watch the console as Elastic Beanstalk creates and runs the necessary resources to run the application. It takes 5-10 minutes for the process to complete.

Elastic Beanstalk creates an Amazon Simple Storage Service (Amazon S3) storage bucket and a security group, launches an Amazon Elastic Compute Cloud (Amazon EC2) instance, and runs the code.

When complete, the screen changes to show the newly created environment. It is ready for you to upload a PHP application.
<img width="708" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/9646e4a9-63a5-4a24-91a0-2293205f19c3">


21. Open a new browser tab or window. Navigate to the [AWS Tutorials and Samples web page] (https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/tutorials.html).

22. On the page, in the second list of downloads, find **PHP – php.zip**. Download the sample **PHP** application to your computer.
- You should now have a file called php.zip.

23. Return to the Elastic Beanstalk console tab.

24. Choose **Upload and deploy**.

25. Choose **Choose file**, navigate to and select the *php.zip* file that you downloaded, and choose **Open**.

26. Choose **Deploy**.
<img width="435" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/7392f1ba-8ae2-40bd-964f-fe0679334901">

The application deploys to the environment using all of the cloud resources Elastic Beanstalk provisioned.

27. To see your PHP website, in the left navigation pane, choose **Go to environment**.
- The web application opens in a new tab.
  <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c1bbc8ff-1e29-4446-9c85-675b75fb2444">


### Task 2. Deploy an application using CloudFormation
28. Return to the AWS Management Console tab.

29. Choose the **Services** menu, locate the **Compute** services, and choose **EC2**.

30. In th left navigation pane, under **Network & Security**, choose **Key Pairs**.

31. Choose **Create key pair**.

32. For **Name**, enter `CFLearner`

33. Choose **Create key pair**.

34. When the download window opens, choose **Cancel**. You do not need to download the file.

35. Choose the **Services** menu, locate the **Management & Governance** services, and choose **CloudFormation**.

The **Stacks** list appears and displays the CloudFormation stacks that were created in your lab environment. Notice the stack whose **Description** says *AWS Elastic Beanstalk environment*. This stack was created automatically when you deployed your application through Elastic Beanstalk.
<img width="736" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/3f100bc2-6bd6-4da9-8b3a-75915df1be4e">

This demonstrates how the two services work together to create an environment to run your code.

36. Choose **Create stack**, and then choose **With new resources (standard)**.

37. In the **Prerequisite** section, choose Use a **sample template**.

38. In the **Select a sample template** section, select **WordPress blog**.

WordPress is web software that you can use to create a website or blog. This template installs a highly available and scalable WordPress deployment using an Amazon Relational Database Service (Amazon RDS) database instance for storage.
<img width="637" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/4c233c42-b9c3-4621-8c26-bd25c90ad038">

39. Select **Next**.

40. For **Stack name**, enter `WordPressStack`

41. In the Parameters section, configure the following:

- **DBPassword:** Enter `Testing1`
- **DBUser:** Enter `testadmin`
- **KeyName:** Choose the **CFLearner** key pair

42. Choose **Next**, and then choose **Next** again.

You will use the default stack options.

43. Review the stack configuration, and then choose **Submit**.

This initiates the deployment of the resources. You can watch the CloudFormation stack events on the Events tab as a complete WordPress site is created.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c17ae159-8f7b-45a4-bac0-9eff803f3ce5">

### Lab complete
Congratulations! You have completed the lab.
