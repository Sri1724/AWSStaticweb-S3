# Static Website Hosting with AWS S3

This project demonstrates how to host a static website using AWS S3. It covers the process of creating an S3 bucket, uploading website files, configuring bucket policies, and setting up the bucket for static website hosting.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Testing](#testing)
- [Resources](#resources)

## Introduction
Hosting a static website on AWS S3 is a cost-effective and scalable solution for serving static content like HTML, CSS, and JavaScript files. This project will guide you through the steps needed to deploy a static website on S3.

## Prerequisites
Before you begin, ensure you have the following:
- An AWS account
- Basic knowledge of HTML/CSS
- AWS CLI installed and configured (optional but recommended)

## Setup

### Step 1: Create an S3 Bucket
1. Log in to the AWS Management Console.
2. Navigate to the S3 service.
3. Click on "Create bucket."
4. Enter a unique bucket name (e.g., `my-static-website-bucket`).
5. Select a region close to your target audience.
6. Keep the remaining settings as default and click "Create bucket."

### Step 2: Upload Website Files
1. Navigate to the newly created bucket.
2. Click on the "Upload" button.
3. Add your website files (e.g., `index.html`, `styles.css`).
4. Click "Upload" to finish.

## Configuration

### Step 3: Configure Bucket for Static Website Hosting
1. In the S3 bucket, go to the "Properties" tab.
2. Scroll down to the "Static website hosting" section.
3. Select "Enable" and choose "Use this bucket to host a website."
4. Enter the name of your index document (e.g., `index.html`).
5. Optionally, specify an error document (e.g., `error.html`).
6. Click "Save."

### Step 4: Set Bucket Policy for Public Access
1. Go to the "Permissions" tab of your S3 bucket.
2. Click on "Bucket Policy" and add the following policy:
    ```json
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
    ```
3. Replace `my-static-website-bucket` with your actual bucket name.
4. Click "Save."

## Deployment

### Step 5: Deploy Your Website
1. Ensure all your website files are uploaded to the S3 bucket.
2. Make sure your bucket policy allows public access to the files.

## Testing

### Step 6: Test Your Website
1. Go to the "Properties" tab of your S3 bucket.
2. Scroll down to "Static website hosting."
3. Copy the "Endpoint" URL.
4. Paste the URL in your web browser to access your static website.

## Resources
- [AWS S3 Static Website Hosting Guide](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)
- [AWS CLI Documentation](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)
- [AWS S3 Bucket Policies](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html)
