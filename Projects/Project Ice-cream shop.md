#        🍨🍓 Website-Icecream-shop 🍧🍦

<img width="756" height="756" alt="13" src="https://github.com/user-attachments/assets/e65bb4fe-d2bc-4971-a3d0-774efa16ab37" />


## Introduction

This project was created as part of a team effort to build an ice cream shop website, which was an amazing experience. In this repository, 
I will walk you through the process step by step to show how everything was created.


## ☁️ Why We Chose Amazon S3

For this project, we decided to use Amazon S3 (Simple Storage Service) to host our website.

Amazon S3 is a reliable and scalable cloud storage service that makes it easy to store and serve static website files such as HTML, CSS, and images. It is widely used for web hosting because of its simplicity and performance.

One of the main advantages is that S3 allows us to host a static website without needing to manage a server. This makes the setup faster and reduces complexity.

Additionally, S3 provides high availability, meaning the website can be accessed at any time, and it can easily scale if the project grows.

Overall, Amazon S3 was a great choice for our ice cream shop website because it is easy to use, cost-effective, and perfect for static web hosting.

<img width="756" height="756" alt="Why we use Amazon S3 " src="https://github.com/user-attachments/assets/307ecb5c-ddf9-4538-8c71-cf1192063884" />

---
## Step by Step Menu

<img width="756" height="756" alt="Step by Step Menu" src="https://github.com/user-attachments/assets/cc87363e-e66b-43ed-95a9-4272c336ada8" />


# 1. Create a bucket

Sign in to the AWS Management Console and open the S3 console: https://console.aws.amazon.com/s3/
Click **Create bucket**.
Enter a bucket name: `static-website-icecream-shop`.
Select a **Region**:
Choose a region close to you for lower latency and cost.
The region also determines your S3 website endpoint.
Leave the default settings and click **Create bucket**.

# 2. Enable static website hosting

Open the S3 console: https://console.aws.amazon.com/s3/

Click **General purpose buckets**.
Select your bucket.
Go to the **Properties** tab.
Scroll to **Static website hosting** and click **Edit**.
Choose **Use this bucket to host a website**.
 Enable static website hosting.
 Enter `index.html` as the **Index document** (case-sensitive).
Click **Save changes**.

<img width="356" height="356" alt="S3 bucket" src="https://github.com/user-attachments/assets/36dd9659-5e6c-4916-814b-dc4d6ef8b214" />

# 2.1 Create Your Website Files Locally 💻

This happens before uploading anything to S3

<!DOCTYPE html>
<html>
<head>
    <title>Ice Cream Shop</title>
</head>
<body>
    <h1>Welcome to our Ice Cream Shop 🍦</h1>
    <p>The sweetest project ever!</p>
</body>
</html>

Save this as: index.html
---

# 3. Add a bucket policy that makes our bucket content publicly available

   <img width="356" height="356" alt="11" src="https://github.com/user-attachments/assets/5999f6e5-9e5d-4eb3-9076-e3be3e36e3bd" />

1. Open the S3 console: https://console.aws.amazon.com/s3/
2. Select your bucket: `static-website-icecream-shop`.
3. Go to the **Permissions** tab.
4. Scroll to **Bucket policy** and click **Edit**.
5. Copy and paste the policy below into the editor.
6. Replace `Bucket-Name` with `static-website-icecream-shop`.
