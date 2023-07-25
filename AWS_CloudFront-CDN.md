## USING CloudFront AS A CDN FOR WEBSITE
### Using CloudFront to create content delivery network (CDN) for a website that is stored in Amazon S3
### Task 1. Create an S3 bucket using the AWS CLI
- In this task, you will create an S3 bucket using the AWS Command Line Interface (AWS CLI). The AWS CLI is an open-source tool that you can use to interact with AWS services using commands in your command line shell.

1. Choose the **Service**s and **Developer Tools** and choose **CloudShell**. <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/61bbc894-38f2-4205-a16f-dbaf0f0d7a12">

   - If a welcome pop-up window appears, choose **Close**.
   - AWS CloudShell is a browser-based shell that gives you command line access to your AWS resources in the selected AWS Region.

2. Copy and paste the following code into a text editor:
   ```text
   cd ~
   aws s3api create-bucket --
   bucket (bucket-name) --
   region us-east-1
   ```
3. In the code that you copied, replace (**bucket-name**) with a unique Domain Name System (DNS)-compliant name for your new bucket.
   - Follow these naming guidelines:
     - The name must be unique across all existing bucket names in Amazon S3.
     - The name must be between 3 and 63 characters long.
     - The name can consist only of lowercase letters, numbers, dots (.), and hyphens (-).
     - The name must begin and end with a letter or number.
     - The name must not be formatted as an IP address (for example, 192.168.5.4).
     - After you create the bucket, you cannot change the name, so choose wisely.
     - Choose a bucket name that reflects the objects in the bucket. This is because the bucket name is visible in the URL that points to the objects that you’re going to put in your bucket.
       <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/130a0dc8-8fdf-4b7b-a091-6f07f79e6f6a">

**Note**: The us-east-1 Region has been entered in the command. When you create a bucket, the best practice is to choose a Region close to you to minimize latency and costs, or to address regulatory requirements. Objects stored in a Region never leave that Region unless you explicitly transfer them to another Region.
4. Run the updated code in the CloudShell terminal.
   - If a pop-up window appears, choose **Paste**.
   - The output should look similar to the following:

    ![image](https://github.com/swatipal1010/AWS_services_handson/assets/110754474/5632556b-6580-4293-90be-287b48b6feba)

**Note** : When you create a bucket with this command, the bucket is open to the public. We recommend that you keep all settings enabled unless you know that you need to turn off one or more of them for your use case, such as to host a public website.

### Task 2. Add a bucket policy
5. In the console, choose the **Services** menu, locate the **Storage** section, and choose **S3**. <img width="652" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/fb0aee00-9a51-458a-8bea-ec409e6a2695">

6. Choose the name of the bucket that you just created. <img width="689" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/1080ab79-ee05-46df-8448-217767c92747">

7. Choose the **Permissions** tab. Under **Block public access (bucket settings)** choose **Edit**. Remove the checkmark for **Block all public access**. Choose **Save changes**. Confirm the changes. <img width="671" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f94f4cb4-f157-4b63-9424-530bf8ed385e"> <img width="609" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/c67ffe37-6847-400e-9ac1-27ff77608aa1">


8. Under **Object Ownership** choose **Edit**. Choose **ACLs enabled**. Check the acknowledgement and choose **Save changes**. <img width="663" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/e315fdc4-9736-49e4-b6e7-6c901c1a275e"> <img width="617" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/517c60e6-c9b6-4ab5-a69b-74ad09502ad2">


9. In the **Bucket policy** section, choose **Edit**. <img width="662" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/760861c3-bdcd-4dba-acd2-0810eaf38ce7">

10. To grant public read access for your website, copy and paste the following bucket policy into the policy editor.
    ```text
    {
    "Version":"2012-10-17",
    "Statement":[
      {
         "Sid":"PublicReadForGetBucketObjects",
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
11. In the policy, replace **example-bucket** with the name of your bucket. <img width="385" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b664bf7f-6721-49df-810a-d774dfed5992">

12. At the bottom of the page, choose **Save changes**.
### Task 3. Upload an HTML document
- In this task, you will upload the index.html file for your webpage to the S3 bucket.
13. Open the context menu (right-click) for the following link, and then choose **Save link as**: [index.html](https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-ACCAIC-1-35050/03-lab-5-cloudfront/s3/index.html)
14. Save the index.html file to your local computer.
15. In the console, choose the **Objects** tab.
16. Upload the index.html file to your bucket.
    - Choose **Upload**.
    - Drag and drop the index.html file onto the upload page. An alternative is to choose **Add files**, navigate to the file, and choose **Open**.
      <img width="626" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/36bcf34f-20a5-4aa6-b63b-e2212fed02ce">

17. Expand the **Permissions** section.
18. Under **Predefined ACLs**, select **Grant public-read access**. <img width="629" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a3d87a8c-9cf6-472c-89cd-affee945b222">

    - A warning message similar to **Granting public-read access is not recommend** appears below the setting you selected.
19. Below the warning, check the box next to **I understand....** <img width="586" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/87282d28-ac5b-4d24-8b8b-09d6fb583579">

20. At the bottom of the page, choose **Upload**.
21. Choose **Close**.
    - The index.html file appears in the **Objects** list. <img width="858" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/321119a0-aa05-491a-8516-60bd258fdc9e">

### Task 4. Test your website
22. Select the **Properties** tab, and scroll down to the **Static website hosting** section. <img width="844" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/4b7b16cd-0403-4def-87fa-d21060597c40">

23. Choose **Edit**.
24. Select **Enable**.
25. In the **Index document** text box, enter `index.html`  <img width="588" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/573f95f4-29cf-4cfe-89a0-fd42acc45749">

26. Select **Save changes**.
27. Scroll down to the **Static website hosting** section again, and copy the **Bucket website endpoint** URL to your clipboard. <img width="838" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/24cb10ef-f119-4cc8-a30c-700747d1c83e">

28. Open a new tab in your web browser, paste the URL you just copied, and press **Enter**. 
    - The **Hello World** webpage should display. You have successfully hosted a static website using an S3 bucket!
      <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/061d3791-efde-45db-b967-33c84405f086">

### Task 5. Create a CloudFront distribution to serve your website
- In this task, you will create an Amazon CloudFront distribution to serve your website.
29. Choose the **Services** menu, locate the **Networking & Content Delivery** section, and choose **CloudFront**. <img width="670" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/deb264ef-7cde-4281-a7e3-8ec446a7656a">

30. Choose Create a **CloudFront Distribution**.
31. Under **Origin**, choose the text box next to **Origin domain** and select the endpoint from your S3 bucket. <img width="454" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a4f12e08-9211-4a96-8fa2-1bb6ecce090f">

32. For **Viewer Protocol Policy**, ensure that **HTTP and HTTPS** is selected. Under **Web Application Firewall (WAF)** choose **Do not enable security protections**. <img width="613" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/3c3c94c2-da8a-40ed-89ec-a1fdf176aa7e">

33. Scroll to the bottom of the page and select **Create Distribution**.
    - A new CloudFront distribution displays in the distributions list. The Status will say Deploying until your website has been distributed. This may take up to 20 minutes.
      <img width="887" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/162554f1-7d4c-4540-b892-b0af139a798e">

    - When the Status says **Enabled**, you can test your distribution.
      <img width="894" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/a0dfde65-bff5-4995-8419-67fc8ba6ae32">

34. Copy the **Domain Name** value for your distribution and save it to a text editor to use in a later step.
35. Create a new HTML file to test the distribution.
    - Find and download an image from the internet.
    - Navigate to your S3 bucket and upload the image file to it, making sure to grant public access as you did when uploading the HTML file earlier in this lab.
      <img width="850" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/ba060fef-3ecc-4086-b680-4d772ab16ad2">

    - Create a new text file using Notepad and copy the following text into it:
      ```text
      <html>
      <head>My CloudFront Test</head>
      <body>
        <p>My test content goes here.</p>
        <p><img src="http://domain-name/object-name" alt="my test image">
      </body>
      </html>
      ```
     - Replace **domain-name** with the domain name that you copied earlier for your CloudFront distribution.
     - Replace **object-name** with the file name of the picture file that you uploaded to your S3 bucket.
     - The edited line of code should look similar to the following:
       ```text
       <p><img src="http://d2f1zrxb2zaf30.cloudfront.net/picture.jpg" alt="my test image">
       ```
     - Save the text file with an HTML extension.
       <img width="590" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/f8434dca-91d3-4872-9265-95fed53ccb58">

36. Use an internet browser to open the HTML file that you just created.
    <img width="960" alt="image" src="https://github.com/shwetasng/AWS_Services/assets/103261868/b7d61bce-20e4-4c98-afe0-f9750a868700">

- If the image that you uploaded shows, your CloudFront distribution was successful. If not, repeat the lab.

