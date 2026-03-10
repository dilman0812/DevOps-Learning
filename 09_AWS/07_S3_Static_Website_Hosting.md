# S3 Static Website Hosting

---

## Introduction

`Amazon S3` can be used to host static websites containing HTML, CSS, JavaScript, and other static assets.

Unlike traditional web servers, S3 provides a serverless way to host static content with high durability and scalability.

Typical use cases include:

- Portfolio websites
- Documentation sites
- Landing pages
- Frontend applications

Basic architecture:

```
User
  |
S3 Static Website Endpoint
  |
Website Files (HTML, CSS, JS)
```

---

## Enabling Static Website Hosting

Static website hosting can be enabled in the bucket configuration.

Required settings:

| Setting | Description |
|------|-------------|
Index Document | Default page (e.g., `index.html`) |
Error Document | Error page (optional) |

Once enabled, S3 provides a **website endpoint**.

Example endpoint:

```
http://bucket-name.s3-website-region.amazonaws.com
```

This endpoint serves the website content stored in the bucket.

---

## Public Access Configuration

Because S3 objects are private by default, the following steps are required to host a public website:

1. Disable block public access settings.
2. Configure bucket policy to allow public read access.
3. Upload website files.

Example bucket policy for public access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```

---

## Website Access Logging

S3 supports **server access logging** to track requests made to a bucket.

Log files can contain information such as:

- Requester IP address
- Request time
- Requested object
- HTTP status code
- User agent

Logging architecture:

```
Website Bucket
      |
      | access logs
      |
Logging Bucket
```

Storing logs in a separate bucket helps with monitoring and auditing website traffic.

---

## Hands-on: Static Website Deployment

A static website was hosted using S3.

### Steps Performed

1. Created a bucket for website files.
2. Created a second bucket to store access logs.
3. Uploaded website content including `index.html`.
4. Enabled static website hosting.
5. Configured public read access using a bucket policy.
6. Enabled server access logging to store logs in the logging bucket.

The website became accessible through the S3 website endpoint.

---

## Testing Versioning Behavior

Versioning was enabled on the website bucket to observe how S3 manages object versions.

Experiment performed:

1. Uploaded an `index.html` file.
2. Uploaded a modified version of `index.html`.
3. Deleted the object to observe version behavior.

Observed results:

```
index.html (version 1)
index.html (version 2)
Delete marker created
```

Previous versions remained available even after deletion.

This demonstrated how versioning protects against accidental file removal.

---

## Benefits of Hosting Static Websites on S3

### High Durability

S3 stores data redundantly across multiple infrastructure components.

### Scalability

Traffic can scale automatically without server management.

### Cost Efficiency

S3 hosting is inexpensive compared to running web servers.

### Simplicity

No need to manage operating systems or web servers.

---

## Cleanup

After completing the experiment, the following resources were removed:

- Website bucket
- Logging bucket
- Uploaded website files

Cleaning up resources helps avoid unnecessary storage costs.

---

## Key Takeaways

During the static website hosting lab:

- Deployed a website using S3
- Configured public access for website files
- Implemented access logging using a separate bucket
- Tested object versioning behavior
- Cleaned up resources after the experiment

This exercise demonstrated how cloud object storage can be used to host and manage static web applications.
