# Creating static-website-icecream-shop


# 1. Start Sandbox


# 2. Accessing the AWS Management Console


Click **Start Lab** to launch the lab.
Wait until you see **"Lab status: ready"**, then close the panel.
Click **AWS** (next to Start Lab) to open the AWS Management Console in a new tab. You will be signed in automatically.
If the tab doesn’t open, allow pop-ups in your browser and try again.
Arrange the AWS Console and these instructions side by side..

# 3. Create a bucket

Sign in to the AWS Management Console and open the S3 console: https://console.aws.amazon.com/s3/
Click **Create bucket**.
Enter a bucket name: `static-website-icecream-shop`.
Select a **Region**:
Choose a region close to you for lower latency and cost.
The region also determines your S3 website endpoint.
Leave the default settings and click **Create bucket**.

<img width="729" height="560" alt="S3 bucket" src="https://github.com/user-attachments/assets/c431fad2-330d-4f18-b600-4ff97e900978" />

# 4. Enable static website hosting

Open the S3 console: https://console.aws.amazon.com/s3/

Click **General purpose buckets**.
Select your bucket.
Go to the **Properties** tab.
Scroll to **Static website hosting** and click **Edit**.
Choose **Use this bucket to host a website**.
 Enable static website hosting.
 Enter `index.html` as the **Index document** (case-sensitive).
Click **Save changes**.

Copy the **Website endpoint URL** to test your site.


5. Add a bucket policy that makes our bucket content publicly available
1. Open the S3 console: https://console.aws.amazon.com/s3/
2. Select your bucket: `static-website-icecream-shop`.
3. Go to the **Permissions** tab.
4. Scroll to **Bucket policy** and click **Edit**.
5. Copy and paste the policy below into the editor.
6. Replace `Bucket-Name` with `static-website-icecream-shop`.
