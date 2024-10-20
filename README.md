Hosting a Static Website on AWS S3
This repository contains instructions and example files to host a static website on AWS S3. AWS S3 (Simple Storage Service) is a cost-effective way to host static websites. Static websites include HTML, CSS, JavaScript, and other files that don’t require server-side processing.

Prerequisites
Before you begin, ensure you have the following:

AWS Account: Create an AWS account.
AWS CLI: Install the AWS CLI and configure it with your AWS credentials.
Website Files: Prepare your static website files (HTML, CSS, JavaScript, etc.).
Step-by-Step Guide
Step 1: Create an S3 Bucket
Sign in to the AWS Management Console.
Navigate to the S3 service.
Click on Create bucket.
Bucket Name: Enter a unique name for your bucket (e.g., my-static-website-bucket).
Region: Choose the AWS region closest to your target audience.
Block Public Access: Uncheck Block all public access to make your website publicly accessible.
Click Create bucket.
Step 2: Upload Website Files to the S3 Bucket
Click on your newly created bucket.
Go to the Objects tab.
Click Upload and upload your static website files (e.g., index.html, style.css, script.js).
Ensure that your index.html file is at the root of your bucket.
Step 3: Enable Static Website Hosting
Go to the Properties tab of your S3 bucket.
Scroll down to Static website hosting and click Edit.
Select Enable.
Hosting Type: Select Host a static website.
Index Document: Enter index.html.
Error Document (optional): Enter error.html if you have a custom error page.
Click Save changes.
Step 4: Set Bucket Policy for Public Access
Go to the Permissions tab of your S3 bucket.
Scroll to Bucket Policy and click Edit.
Add the following policy to make your bucket publicly readable:
json
Copy code
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
Click Save changes.
Step 5: Access Your Website
Go back to the Properties tab of your S3 bucket.
Under Static website hosting, copy the Bucket website endpoint.
Open this URL in your browser to view your hosted static website.
Optional: Set Up a Custom Domain (Using Route 53)
Purchase a domain from AWS Route 53 or any other domain registrar.
In Route 53, create a Hosted Zone for your domain.
Create an A record in the Hosted Zone and set it to point to your S3 website endpoint.
Update the domain's Name Servers (NS) with those provided in the Route 53 hosted zone.
It may take a few minutes to hours for the changes to propagate.
Optional: Enable HTTPS (Using Amazon CloudFront)
To secure your website with HTTPS, you can use Amazon CloudFront:

Navigate to CloudFront in the AWS console.
Click Create Distribution.
Choose Web and enter your S3 bucket’s Website Endpoint.
For SSL/TLS Certificate, select Custom SSL Certificate (choose or upload an SSL certificate from ACM).
Click Create Distribution.
Update your domain's DNS settings to point to the CloudFront distribution.
Cleaning Up
To avoid unnecessary charges, make sure to:

Delete the S3 bucket when you no longer need the website.
Remove the CloudFront distribution if you set it up.
Clean up Route 53 entries if using a custom domain.
Troubleshooting
403 Forbidden Error: Ensure that your S3 bucket policy allows public read access.
Page Not Found: Verify that the index.html is correctly uploaded and named.
Changes Not Reflected: S3 caches files for faster delivery. Try clearing the cache or updating the file with a new name.
Resources
AWS S3 Documentation
Hosting a Static Website on S3
Amazon CloudFront Documentation
License
This project is licensed under the MIT License. See the LICENSE file for details.

