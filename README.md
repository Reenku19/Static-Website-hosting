**Hosting a Static Website on AWS S3**

This repository contains instructions and example files to host a static website on AWS S3. AWS S3 (Simple Storage Service) is a cost-effective way to host static websites. Static websites include HTML, CSS, JavaScript, and other files that don’t require server-side processing.

**Prerequisites**

Before you begin, ensure you have the following:

•	AWS Account: Create an AWS account.

•	AWS CLI: Install the AWS CLI and configure it with your AWS credentials.

•	Website Files: Prepare your static website files (HTML, CSS, JavaScript, etc.).

**Step-by-Step Guide**

**Step 1: Create an S3 Bucket**

1.	Sign in to the AWS Management Console.
2.	Navigate to the S3 service.
3.	Click on Create bucket.
4.	Bucket Name: Enter a unique name for your bucket (e.g., my-static-website-bucket).
5.	Region: Choose the AWS region closest to your target audience.
6.	Block Public Access: Uncheck Block all public access to make your website publicly accessible.
7.	Click Create bucket.

**Step 2: Upload Website Files to the S3 Bucket**
1.	Click on your newly created bucket.
2.	Go to the Objects tab.
3.	Click Upload and upload your static website files (e.g., index.html, style.css, script.js).
4.	Ensure that your index.html file is at the root of your bucket.

**Step 3: Enable Static Website Hosting**
1.	Go to the Properties tab of your S3 bucket.
2.	Scroll down to Static website hosting and click Edit.
3.	Select Enable.
4.	Hosting Type: Select Host a static website.
5.	Index Document: Enter index.html.
6.	Error Document (optional): Enter error.html if you have a custom error page.
7.	Click Save changes.

**Step 4: Set Bucket Policy for Public Access**
1.	Go to the Permissions tab of your S3 bucket.
2.	Scroll to Bucket Policy and click Edit.
3.	Add the following policy to make your bucket publicly readable:
json

{

  "Version": "2012-10-17",
  
  "Statement": [
  
    {
    
      "Sid": "PublicReadGetObject",
      
      "Effect": "Allow",
      
      "Principal": "*",
      
      "Action": "s3:GetObject",
      
      "Resource": "arn:aws:s3:::my-static-website-bucket/*"
    
    }
  
  ]

}

Replace my-static-website-bucket with the name of your S3 bucket.

4.	Click Save changes.

**Step 5: Access Your Website**

•	Go back to the Properties tab of your S3 bucket.
•	Under Static website hosting, copy the Bucket website endpoint.
•	Open this URL in your browser to view your hosted static website.

**Cleaning**

To avoid unnecessary charges, make sure to:
•	Delete the S3 bucket when you no longer need the website.
•	Remove the CloudFront distribution if you set it up.
•	Clean up Route 53 entries if using a custom domain.

**Troubleshooting**

•	403 Forbidden Error: Ensure that your S3 bucket policy allows public read access.
•	Page Not Found: Verify that the index.html is correctly uploaded and named.
•	Changes Not Reflected: S3 caches files for faster delivery. Try clearing the cache or updating the file with a new name.

**Resources**

•	AWS S3 Documentation
•	Hosting a Static Website on S3
•	Amazon CloudFront Documentation

**License**

This project is licensed under the MIT License. See the LICENSE file for details.

