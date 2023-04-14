## Session 1: AWS Overview and Common Services

### Content
* Introduction to Cloud Computing
* Overview of common Services
	* Amazon EC2 (Elastic Compute Cloud)
	* Amazon S3 (Simple Storage Service)
	* Amazon RDS (Relational Database Service)
	* AWS Lambda (Serverless Computing)
	* Route53 (Virtual Private Cloud)
	

## Session 2: Infrastructure as Code - Fundamentals

### Content
* AWS CloudFormation
* Terraform
* Deploying infrastructure with github actions 

E.g. Cloudformation
```
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  HelloWorldBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: hello-world-your-unique-id
      AccessControl: PublicRead

  HelloWorldBucketPolicy:
    Type: AWS::S3::BucketPolicy
    Properties:
      Bucket: !Ref HelloWorldBucket
      PolicyDocument:
        Version: '2012-10-17'
        Statement:
          - Effect: Allow
            Principal: '*'
            Action:
              - 's3:GetObject'
            Resource: !Sub 'arn:aws:s3:::${HelloWorldBucket}/*'
```

Terraform HCL
```
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "hello_world" {
  bucket = "hello-world-your-unique-id"
  acl    = "public-read"
}

resource "aws_s3_bucket_policy" "hello_world_policy" {
  bucket = aws_s3_bucket.hello_world.id

  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Action = [
          "s3:GetObject"
        ]
        Effect = "Allow"
        Resource = [
          "${aws_s3_bucket.hello_world.arn}/*"
        ]
        Principal = "*"
      }
    ]
  })
}

```

## Session 3: Amazon EC2

### Content
* AMIs and EBS storage
* Creating and configuring Amazon EC2 instances

### Hands-on
* Write a CloudFormation/Terraform script to create and configure an EC2 instance


## Session 4: Amazon S3
### Content
* Buckets, objects, and storage classes
* Data management (lifecycle policies, versioning, and encryption)

### Hands-on
* Write a CloudFormation/Terraform script to create and configure an Amazon S3 bucket

## Session 5: Amazon RDS

### Content
* Supported database engines
* RDS instances, storage, and security
* Backup, recovery, and monitoring

### Hands-on
Write a CloudFormation/Terraform script to create and configure an Amazon RDS instance

## Session 6: AWS Lambda

### Content
* Overview of AWS Lambda
* Lambda functions and triggers
* Creating and deploying Lambda functions
* Monitoring and troubleshooting Lambda functions

### Hands-on
Write a CloudFormation/Terraform script to create and configure an AWS Lambda function




## Session 8: Amazon Route 53
### Overview
* Overview of Amazon Route 53
* DNS concepts (domains, subdomains, and records)
* Registering domain names and managing DNS records
* Routing policies and health checks

### Hands-on
Write a CloudFormation/Terraform script to create and configure Route 53 resources
