# Introduction to Amazon S3
## Project Overview

Amazon Simple Storage Service (S3) is one of the most fundamental and widely-used services in the AWS cloud computing platform. As an object storage service, S3 offers industry-leading scalability, data availability, security, and performance for a wide variety of use cases, including data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

## Project Objectives

This hands-on project is designed to provide participants with a comprehensive introduction to Amazon S3 and its core functionalities. Through practical exercises, participants will gain firsthand experience working with this essential cloud storage service. The project focuses on building foundational knowledge that is critical for anyone pursuing cloud computing or working with AWS infrastructure.

## Learning Scope

The project curriculum covers the essential aspects of S3 management, beginning with bucket creation and configuration through the AWS Management Console. Participants will learn how to:
- Create and properly configure S3 buckets, understanding the significance of region selection and naming conventions
- Upload, organize, and manage objects within these buckets
- Implement version control to maintain object history and prevent accidental data loss
- Configure granular permissions to ensure proper access control and security
- Design and apply lifecycle policies to automate data management processes

## Practical Applications

By mastering these S3 fundamentals, participants will develop skills directly applicable to real-world scenarios such as:
- Building secure cloud storage solutions for applications and websites
- Implementing data backup and recovery strategies
- Optimizing storage costs through intelligent tiering and lifecycle management
- Configuring proper access controls for sensitive data
- Maintaining data integrity through version control systems

This project serves as an essential stepping stone for anyone beginning their AWS journey, providing the practical S3 knowledge that forms the foundation for more advanced cloud architectures and solutions. The hands-on approach ensures participants not only understand theoretical concepts but can immediately apply them in professional environments.

## Part A

1. ### 🧭 Navigation

![Navigating to S3](./img/1.%20navigating%20to%20s3.jpg)  
We begin by locating the Amazon S3 service via the AWS Console.

---

2. ### 🪣 Create an S3 Bucket

![Click on Create](./img/2.%20click%20on%20create.jpg)  
- Click **Create bucket** to begin the setup.
![Bucket Configuration](./img/3.%20choosing%20a%20bucket%20name.jpg)
![Bucket Configuration](./img/4.%20choosing%20a%20bucket%20name%202.jpg) 
![Bucket Configuration](./img/5.%20choosing%20a%20bucket%20name%202.jpg)
![Bucket Configuration](./img/6.%20Successful.jpg) 
![Bucket Configuration](./img/7.%20Successful.jpg)  
Use a globally unique bucket name. Keep **ACLs disabled** and **block all public access** enabled to protect the bucket.

---

## Part B

1. ### Using Notepad create a file on your laptop with some data
![create a file](./img/8.%20text%20file%20created.jpg)

2. ### Upload an Object (File, media etc)

![Upload an Object](./img/9.%20click%20on%20upload.jpg)

3. ### Add file to bucket 
![Upload an Object](./img/10.%20Add%20files.jpg)
This allow you to upload or add file to the created bucket.
![Upload an Object](./img/11.%20upload%20the%20file.jpg)
![Upload an Object](./img/12.%20success%20of%20upload.jpg)
![Upload an Object](./img/13.%20success%20of%20upload.jpg)

---

## Part C

1. ### Object Versioning
Navigate back to the created bucket and click on properties as in the image
![Versioning](./img/14.%20Versioning-clickon-property.jpg)

- Click on Edit to see the versioning
![Versioning](./img/15.%20click%20on%20edit.jpg)

- Enable Bucket versioning and click on save
![Upload an Object](./img/16.%20enable%20versioning.jpg)
![Upload an Object](./img/17.%20Versioning%20successful.jpg)

2. ### Upload the second file to the bucket (edited)

![Upload an Object](./img/18.%20Second%20copy%20uploaded.jpg)
![Upload an Object](./img/19.%20second%20document%20successful.jpg)

3. ### Show the version history
Toggle the show version button to see the version history
![Upload an Object](./img/20.%20Versioning%20complete.jpg)

---

# Part D

1. ### Lets add permissions for the bucket
Navigate to permission section of the bucket and "Block all Public Access" by unchecking the box, then click on Edit, SAVE the changes.

![Upload an Object](./img/21.%20apply%20permission.jpg)
![Upload an Object](./img/22.%20Editing%20permission.jpg)
- Confirm the permission
![Upload an Object](./img/23.%20Confirm%20and%20submit.jpg)
![Upload an Object](./img/24.%20Success.jpg)

**Note:** Once this is confirm, you have allow your file to be publicly accessble to anyone that have the public url and you are aware and responsible for any implication.

2. Lets add policy to the bucket to specify action you want your client to perform
![Upload an Object](./img/25.%20Editing%20bucket%20policy.jpg)
- Click on Edit as in the image
**Next** Click on policy generator 
![Upload an Object](./img/26.%20generating%20policy.jpg)

**Fellow** The images below to create your bucket policy.

![Upload an Object](./img/27.%20ARN%20POLICY%20GENERATOR.jpg)
![Upload an Object](./img/28.%20ADD%20POLICY.jpg)
- Copy the created policy and click close
![Upload an Object](./img/29.%20COPY%20POLICY.jpg)

Attach this policy to a user or group:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowS3AccessToSpecificBucket",
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket",
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": [
        "arn:aws:s3:::3mttdevbuckettesting",
        "arn:aws:s3:::3mttdevbuckettesting/*"
      ]
    }
  ]
}
```
**Navigate back to the AWS Console**
![Upload an Object](./img/30.%20Attach%20policy.jpg)
Paste the copied permission policy created in the policy generator page. 

- You will see a success page like the image below.
![Upload an Object](./img/30.%20Bucket%20policy%20added%20successfully.jpg)

3. Now navigate back to the bucket 
![Upload an Object](./img/31.%20version.jpg)
- Click on the first version
![Upload an Object](./img/32.%20Object%20URL.jpg)
- Click on the object url 
![Upload an Object](./img/33.%20URL%20resolved.jpg)

4. Navigate back to the bucket 
Click on the sceond version of the object
![Upload an Object](./img/34.%20version.jpg)
- Click on the object url
![Upload an Object](./img/35.%202nd%20Object%20URL.jpg)
![Upload an Object](./img/36.%202nd%20URL%20resolved.jpg)

---

## Part E
1. ### Create Lifecycle Policies
Now, navigate to the management section of the bucket.
- Click on Lifecycle Policies
![Upload an Object](./img/37.%20Creating%20lifecycle%20rule.jpg)

2. ### Lifecycle rule configuration 
Assign a unique name to the rule and choose the limit scope of the rule using one or more filters
![Upload an Object](./img/38.%20Creating%20lifecycle%20rule.jpg)
![Upload an Object](./img/39.%20Creating%20lifecycle%20rule.jpg)

- Click on create lifecycle rule
![Upload an Object](./img/40.%20Creating%20lifecycle%20rule.jpg)

- Successfully created the lifecycle rule
![Upload an Object](./img/41.%20Creating%20lifecycle%20rule%20%20successful.jpg)

Security Best Practices
- Least Privilege
- HTTPS Enforcement
- Roles Instead of Users
- Bucket Versioning
- Default Encryption
- Public Access Block


## Project Reflection
Key Learnings
Policy Granularity Matters: Separating bucket-level and object-level permissions prevents overprivileged access

Versioning is Critical: Protects against accidental deletions and ransomware

Encryption Hierarchy: SSE-KMS with bucket keys reduces costs while maintaining security

Temporary Credentials: Roles provide more secure access than long-term keys

### Maintenance Guide
Policy Versioning: Always create new policy versions instead of editing live policies

Quarterly Reviews: Audit permissions using IAM Access Analyzer

Credential Rotation: Use roles instead of long-term credentials



