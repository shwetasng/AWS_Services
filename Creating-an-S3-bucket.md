# Module 4 Lab 2: Creating an S3 Bucket
## Lab overview
Follow these steps to create an Amazon Simple Storage Service (Amazon S3) bucket to host a static website.

A static website is fixed and displays the same content for each user. In contrast, a dynamic website uses advanced programming to provide user interaction and display different content depending on the user's selections.

## Duration
This lab requires approximately **30 minutes** to complete.

## Access the AWS Management Console
1. To start the lab session, choose :arrow_forward: Start Lab in the upper-right corner of the page.

    - The lab session starts.
    
    - A timer displays in the upper-right corner of the page and shows the time remaining in the session.

**Tip:** To refresh the session length at any time, choose **Start Lab** again before the timer reaches 0:00.

Before continuing, wait until the lab environment is ready. The environment is ready when the lab details appear on the right side of the page and the circle icon next to the AWS link in the upper-left corner turns green.

2. To return to these instructions, choose the  Readme link in the upper-right corner.

3. To connect to the AWS Management Console, choose the AWS link in the upper-left corner, above the terminal window.

A new browser tab opens and connects you to the AWS Management Console.

**Tip:** If a new browser tab does not open, a banner or icon is usually at the top of your browser with the message that your browser is preventing the site from opening pop-up windows. Choose the banner or icon, and then choose **Allow pop-ups**.

**Note:** You are using the console through the lab environment, so you are not incurring any actual costs. However, in the real world, when using a personal or business account to access the console, users incur charges for use of specific AWS services.

## Task 1. Create an S3 bucket
4. Choose the **Services** menu, locate the **Storage** services, and select **S3**.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f4e329c3-1bc2-45dc-a2af-f4825a1aab36">

5. Select **Create bucket** on the right side of the page.

6. For **Bucket name**, enter a unique Domain Name System (DNS)-compliant name for your new bucket.
<img width="731" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/0c0d523f-87b7-4184-9238-d6035da3b2ad">

Follow these naming guidelines:

- The name must be unique across all existing bucket names in Amazon S3.
- The name must only contain lowercase characters.
- The name must start with a letter or number.
- The name must be between 3 and 63 characters long.
- After you create the bucket, you cannot change the name, so choose wisely.
- Choose a bucket name that reflects the objects in the bucket. This is because the bucket name is visible in the URL that points to the objects that you’re going to put in your bucket.
7. For **Region**, choose the AWS Region where you want the bucket to reside.

Choose a Region close to you to minimize latency and costs, or to address regulatory requirements. Objects stored in a Region never leave that Region unless you explicitly transfer them to another Region.

8. Uncheck the Block all public access box because you want to be able to test if the website is working.
<img width="620" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/5da6ad34-390e-4268-b64d-a5bf55b6b748">

A warning message similar to Turning off block all public access might result in this bucket and the objects within becoming public appears below the security setting you deselected.

9. Below the warning, check the box next to I acknowledge that....
<img width="584" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/20d41bfa-59c6-41e8-bd7f-38ca5270353e">

10. Scroll to the bottom of the page, and select Create bucket.
<img width="619" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/50a0b8e9-23c4-4ce6-8e4a-ff000e292495">

Your new bucket appears in the Buckets list.

## Task 2. Add a bucket policy to make the content publicly available
11. Choose the link for your bucket's name, and then select the **Permissions** tab.
<img width="856" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/5531db69-5415-4c5e-aafc-39405e9dc25f">

12. In the **Bucket policy** section, choose Edit.
<img width="851" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/209cf10f-eed1-4f46-9615-8edd845118ab">

13. To grant public read access for your website, copy the following bucket policy, and paste it in the policy editor.
```text
{
    "Version":"2012-10-17",
    "Statement":[
        {
            "Sid":"PublicReadGetObject",
            "Effect":"Allow",
            "Principal":"*",
            "Action":[
                "s3:GetObject"
            ],
            "Resource":[
                "arn:aws:s3:::example-bucket/*"
            ]
        }
    ]
}
```

14. In the policy, replace example-bucket with the name of your bucket.<img width="564" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/5983a865-d8c3-4de5-a643-3dd823c88cef">

15. Select Save changes.
## Task 3. Upload an HTML document
In this task, you upload an HTML document to your new bucket.

16. Open the context menu (right-click) for the following link, and then choose **Save link as:** index.html

17. Save the index.html file to your local computer.

18. In the console, choose the **Objects** tab.
<img width="851" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/d064c79b-d667-4fce-a41f-37290b14a9ba">

19. Upload the index.html file to your bucket.

    - Choose **Upload**.<img width="836" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/24acf31f-239a-4384-ba3d-9891473b1e56">

    - Drag and drop the index.html file onto the upload page.<img width="629" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b203ec2a-ab92-4c84-b6b9-aa9018cb6be6">

    - As an alternative, choose **Add files**, navigate to the file, and choose **Open**.
20. Expand the **Properties** section.

This section lists the storage classes that are available in Amazon S3. You will learn more about storage classes later, but take a minute to review them now.
Ensure that the **Standard** storage class is selected.
<img width="626" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/3aea137a-e695-47ac-9164-2dfb755eb6c9">

21. At the bottom of the page, choose **Upload**.
<img width="628" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/d780e9eb-91dd-4835-a353-5e2e715ffafb">

22. Choose **Close**.
<img width="904" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/98f65ed5-7dfe-41d8-bc80-e8607d0103d3">

The index.html file appears in the Objects list.

## Task 4. Test your website
23. Select the **Properties** tab, and scroll down to the **Static website hosting** section.
<img width="841" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ae2d72ef-a05f-4877-8f96-249a4452d52c">

24. Choose **Edit**.

25. Select **Enable**.
<img width="614" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ebd8cabd-a9f5-4ba3-9aea-e1f1870dc750">

26. In the **Index document** text box, enter index.html
<img width="458" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a14e9b34-96c0-4538-a29d-62d6763dbbb7">

27. Select **Save changes**.

28. Scroll down to the **Static website hosting** section again, and copy the **Bucket website endpoint** URL to your clipboard.
<img width="838" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/74aea6c5-32f4-47c8-a5be-0813ab42ae57">

29. Open a new tab in your web browser, paste the URL you just copied, and press **Enter**.
<img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/35ab3dc2-0443-47c3-b92b-0351d86a3247">

The **Hello World** webpage should display. You have successfully hosted a static website using an S3 bucket!

## Lab complete
Congratulations! You have completed the lab.

30. Log out of the AWS Management Console.

    - In the upper-right corner of the page, choose your user name. Your user name begins with voclabs/user.
    - Choose Sign Out.
31. Choose End Lab at the top of this page, and then select Yes to confirm that you want to end the lab.
