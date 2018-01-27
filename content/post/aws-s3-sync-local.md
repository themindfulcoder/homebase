---
title: "Aws S3 Sync Local"
date: 2017-12-05
draft: true
---

# Sync a local folder to an AWS S3 bucket

I've been playing around with AWS services, the simplest of which is probably S3, the Simple Storage Service. In fact, this website is provided using an AWS S3 bucket.

### What is an AWS S3 bucket?

An AWS S3 bucket is essentially a folder like on your computer but in the cloud. You can store almost anything in a S3 bucket be it images, mp3's, videos or documents.

### The problem:

Using the AWS web console can be pretty tedious when you have a complicated structure in your S3 bucket with files changing in each of the "sub-directories" all the time. So the question became, how can I easily move my files to my S3 bucket without manually uploading each sub-directory

### AWS Command Line Integration tool

The AWS CLI came to my rescue! You can find out more about the AWS CLI [here](https://github.com/aws/aws-cli)

It offered me some simple commands for interacting with their services, S3 being one of them. To get started, you install it using the linked provided just above. Once installed, get it configured using `aws configure` it'll ask you some questions, like your *AccessKey* and *SecretKey* which you can generate in AWS console. Here comes the magic:

``` shell
aws s3 sync path/to/my/local/folder s3://my-bucket-name
```

It detects which files are not identical and uploads just the files which have changed. Now I've got time for another cup of coffee!