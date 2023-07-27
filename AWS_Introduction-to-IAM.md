## AWS Identity and Access Management (IAM)
- In this lab, you will explore users, groups, and policies in the AWS Identity and Access Management (IAM) service.

### Task 1. Explore the users and groups
- In this task, you will explore the users and groups that have already been created for you in IAM.
1. First, note the Region that you are in; for example, **N. Virginia**. The Region is displayed in the upper-right corner of the console page. 
<img width="946" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/6dd80e73-fb7c-4e4f-9f87-411bf4827cf1">

   - You might need this information later in the lab.
2. Choose the Services menu, locate the **Security, Identity, & Compliance** services, and choose **IAM**. 
<img width="652" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/1e141f47-30eb-413a-b98f-8b04d6169a60">

3. In the navigation pane on the left, choose **Users**. 
<img width="200" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f893eb62-1f6d-430e-8fa0-f36044685f15">

   - The following IAM users have been created for you:
     - user-1
     - user-2
     - user-3
4. Choose the name of **user-1**.
   - This brings you to a summary page for user-1. 
<img width="661" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/3fcdabd0-44d2-4caf-8d04-5c14a728f433">

   - The Permissions tab will be displayed. 
<img width="655" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/17297c88-db1b-4d3e-b430-082b8a9bcfdb">

   - Notice that user-1 does not have any permissions.
   - Choose the Groups tab.
   <img width="669" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b0df8664-07a0-48fb-9a40-f612438b1618">

   - Notice that user-1 also is not a member of any groups.
5. Choose the **Security credentials** tab.
   - Notice that user-1 is assigned a **Console password**. This allows the user to access the AWS Management Console.
     <img width="664" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/add545be-0acf-4814-92ed-fc09b0115ae9">

6. In the navigation pane on the left, choose **User groups**. 
<img width="677" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/274d5170-dba9-41b6-9f8c-967477eb6bb0">

   - The following groups have already been created for you:
     - EC2-Admin
     - EC2-Support
     - S3-Support
7. Choose the name of the **EC2-Support** group.
   - This brings you to the summary page for the **EC2-Support** group.
8. Choose the **Permissions** tab. 
<img width="659" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/1392c405-9b0c-4f0e-b850-f7e106081676">

   - This group has a managed policy called **AmazonEC2ReadOnlyAccess** associated with it. Managed policies are prebuilt policies (built either by AWS or by your administrators) that can be attached to IAM users and groups. When the policy is updated, the changes to the policy are immediately applied against all users and groups that are attached to the policy.
9. Under **Policy Name**, choose the link for the **AmazonEC2ReadOnlyAccess** policy.
10. Choose the **{} JSON** tab. 
<img width="672" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/3e404932-187b-4795-aca0-fd8f77547bf8">

- A policy defines what actions are allowed or denied for specific AWS resources. This policy is granting permission to *List* and *Describe* (view) information about Amazon Elastic Compute Cloud (Amazon EC2), Elastic Load Balancing, Amazon CloudWatch, and Amazon EC2 Auto Scaling. This ability to view resources, but not modify them, is ideal for assigning to a support role.
 - Statements in an IAM policy have the following basic structure:
   - **Effect** says whether to *Allow* or *Deny* the permissions.
   - **Action** specifies the API calls that can be made against an AWS service (for example, *cloudwatch:ListMetrics*).
   - **Resource** defines the scope of entities covered by the policy rule (for example, a specific Amazon Simple Storage Service [Amazon S3] bucket or Amazon EC2 instance; an asterisk [ * ] means *any resource*).
11. In the navigation pane on the left, choose **User groups**.
12. Choose the name of the **S3-Support** group.
13. Choose the **Permissions** tab. 
<img width="653" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/fced82bc-4168-45ac-b8b0-d34badd938df">

   - The S3-Support group has the **AmazonS3ReadOnlyAccess** policy attached.
14. Under **Policy Name**, choose the link for the **AmazonS3ReadOnlyAccess** policy.
15. Choose the **{} JSON** tab. 
<img width="661" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/773c81de-5902-4dd1-acbd-637f16bc89a6">

   - This policy has permissions to *Get* and *List* for *all* resources in Amazon S3.
16. In the navigation pane on the left, choose **User groups**.
17. Choose the name of the **EC2-Admin** group.
18. Choose the **Permissions** tab. 
<img width="660" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/6b1766c9-50a4-4e01-b8c8-3d906dd7a9da">

   - This group is different from the other two. Instead of a managed policy, the group has an *inline policy*, which is a policy assigned to just one user or group. Inline policies are typically used to apply permissions for specific situations.
19. Under **Policy Name**, choose the name of the **EC2-Admin-Policy** policy.
20. Choose the **JSON** tab. 
<img width="667" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/46f1e684-39fb-4b49-b2ed-3388da9fc111">

   - This policy grants permission to *Describe* information about Amazon EC2 instances, and also the ability to *Start* and *Stop* instances.
21. At the bottom of the screen, choose **Cancel** to close the policy.


### Business scenario
- For the remainder of this lab, you will work with these users and groups to enable permissions that support the following business scenario.
- Your company is growing its use of AWS services, and is using many Amazon EC2 instances and Amazon S3 buckets. You want to give access to new staff depending upon their job function, as indicated in the following table:
<img width="602" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a26502ca-d661-4f42-943f-b86ef67f235f">



### Task 2. Add users to groups
- You have recently hired ***user-1*** into a role where they will provide support for Amazon S3. You will add them to the ***S3-Support*** group so that they inherit the necessary permissions via the attached ***AmazonS3ReadOnlyAccess*** policy.
- Ignore any **"not authorized"** errors that appear during this task


### Add user-1 to the S3-Support group
22. In the left navigation pane, choose **User groups**.
23. Choose the name of the **S3-Support** group.
24. On the **Users** tab, choose **Add users**. 
<img width="664" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/560c02e1-c7ec-4e7e-8396-11534aa98b6e">

25. Select  **user-1**, and choose **Add users**. 
<img width="664" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ed8078da-b3e2-491c-9bf1-98bd8d853df6">

- On the **Users** tab, notice that *user-1* has been added to the group.


### Add user-2 to the EC2-Support group
- You have hired ***user-2*** into a role where they will provide support for Amazon EC2. You will add them to the ***EC2-Support group*** so that they inherit the necessary permissions via the attached ***AmazonEC2ReadOnlyAccess*** policy.
26. Use what you learned from the previous steps to add *user-2* to the *EC2-Support* group. 
<img width="661" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c5db9422-f77a-41ba-8f34-9acffb380d16">

   - *user-2* should now be part of the *EC2-Support* group.


### Add user-3 to the EC2-Admin group
- You have hired ***user-3*** as your Amazon EC2 administrator to manage your EC2 instances. You will add them to the ***EC2-Admin*** group so that they inherit the necessary permissions via the attached ***EC2-Admin-Policy***.
27. Use what you learned from the previous steps to add *user-3* to the *EC2-Admin group*. 
<img width="659" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/80d81484-14ab-49ba-918c-58c916c04421">

   - *user-3* should now be part of the *EC2-Admin group*.
28. In the navigation pane on the left, choose **User groups**.
    - Each group should have a **1** in the **Users** column. This indicates the number of users in each group. 
   <img width="674" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/41249a1f-13b6-4e64-8410-a01019e384ae">

   - If you do not have a **1** for the **Users** column for a group, revisit the previous steps to ensure that each user is assigned to a group, as shown in the table in the **Business scenario** section.


### Task 3. Sign in and test users
- In this task, you will test the permissions of each IAM user in the console.

#### Get the console sign-in URL
29. In the navigation pane on the left, choose **Dashboard**.
    - Notice the **Sign-in URL for IAM users** in this account section at the top of the page. 
<img width="191" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/e722dbe5-7dc1-4653-9aaa-49310a55a595">

- The sign-in URL looks similar to the following:
  - **https://123456789012.signin.aws.amazon.com/console**
  - This link can be used to sign in to the AWS account that you are currently using.
30. Copy the sign-in link to a text editor.

#### Test user-1 permissions
31. Open a private or incognito window in your browser.
32. Paste the sign-in link into the private browser, and press ENTER. 
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c8e01095-ea04-4687-906f-2c22ac3c359a">

- You will now sign-in as *user-1*, who has been hired as your Amazon S3 storage support staff.
33. Sign in with the following credentials:
    - **IAM user name**: `user-1`
    - **Password**: `Lab-Password1`
      <img width="950" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/de75810a-c00a-4415-aa6a-36aa4ecc2096">

34. Choose the **Services** menu, and choose **S3**.
35. Choose the name of one of your buckets, and browse the contents.
    - Because this user is part of the S3-Support group in IAM, they have permissions to view a list of Amazon S3 buckets and their contents.
    - Now, test whether the user has access to Amazon EC2.
36. Choose the **Services** menu, and choose **EC2**.
37. In the left navigation pane, choose **Instances**. 
<img width="766" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/3be1e5bc-8a12-45cb-9839-a07cfaf262fb">

- You cannot see any instances. Instead, an error message says *you are not authorized to perform this operation*. This user has not been assigned any permissions to use Amazon EC2.
    - You will now sign in as *user-2*, who has been hired as your Amazon EC2 support person.
38. First, sign out *user-1* from the console:
    - In the upper-right corner of the page, choose **user-1**.
    - Choose **Sign Out**.

#### Test user-2 permissions
39. Paste the sign-in link into the private browser again, and press ENTER.
40. Sign in with the following credentials:
    - **IAM user name**: `user-2`
    - **Password:** `Lab-Password2`
41. Choose the **Services** menu, and choose **EC2**.
42. In the navigation pane on the left, choose **Instances**. 
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/e063e2d5-8eac-47d7-9106-eca6f0362bdf">

- You are now able to see an EC2 instance. However, you cannot make any changes to Amazon EC2 resources because you have read-only permissions.
- If you cannot see an EC2 instance, then your Region might be incorrect. In the upper-right corner of the page, choose the Region name, and then choose the Region that you were in at the beginning of the lab (for example, **N. Virginia**).
43. Select the EC2 instance.
44. Choose the **Instance state** menu, and then choose **Stop instance**. 
<img width="774" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/34c37a42-e509-45d3-a2fe-ceb22898d11b">

45. To confirm that you want to stop the instance, choose **Stop**.
    - An error message appears and says that *You are not authorized to perform this operation*. This demonstrates that the policy only allows you to view information without making changes.
      <img width="764" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/14549ec1-d072-4e2f-824b-194da4c7989b">

    - Next, check if *user-2* can access Amazon S3.
46. Choose the **Services** menu, and choose **S3**.
    - An error message says *You don't have permissions to list buckets because user-2 does not have permissions to use Amazon S3*
      <img width="638" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/5664a81e-63db-4eec-a838-7980ba3f26f9">

    - You will now sign-in as *user-3*, who has been hired as your Amazon EC2 administrator.
47. First, sign out *user-2* from the console:
    - In the upper-right corner of the page, choose **user-2**.
    - Choose **Sign Out**.
#### Test user-3 permissions
48. Paste the sign-in link into the private browser again, and press ENTER.
49. Sign in with the following credentials:
    - **IAM user name:** `user-3`
    - **Password:** `Lab-Password3`
50. Choose the **Services** menu, and choose **EC2**.
51. In the navigation pane on the left, choose **Instances**.
    - An EC2 instance is listed. As an Amazon EC2 Administrator, this user should have permissions to *Stop* the EC2 instance.
    - If you cannot see an EC2 instance, then your Region might be incorrect. In the upper-right corner of the page, choose the Region name, and then choose the Region that you were in at the beginning of the lab (for example, **N. Virginia**)
52. Select the EC2 instance.
53. Choose the **Instance state** menu, and then choose **Stop instance**.
54. To confirm that you want to stop the instance, choose **Stop**.
    <img width="776" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/4841fbe2-14db-4e1a-934d-c17d0039c3d9">

    - This time, the action is successful because *user-3* has permissions to stop EC2 instances. The **Instance state** changes to *Stopping and starts to shut down*.
55. Close your private browser window.
