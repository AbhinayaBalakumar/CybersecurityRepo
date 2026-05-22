<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Encrypt Data with AWS KMS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-kms)

**Author:** Abhinaya Balakumar  
**Email:** balakumarabhinaya@gmail.com

---

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/aws-security-kms_w0x1y2z3)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS KMS to encrypt and protect cloud data securely. The goal is to learn how encryption keys work, secure a DynamoDB database with KMS, test encrypted data access, and understand how AWS controls authorized and unauthorized access to sensitive information.

### Tools and concepts

Services I used include AWS Key Management Service (KMS), Amazon DynamoDB, and AWS Identity and Access Management (IAM).

Key concepts I learned include encryption, data at rest, customer managed keys, key policies, IAM permissions, and transparent data encryption, along with how KMS enforces secure access control separately from DynamoDB permissions.

### Project reflection

This project took me approximately 1–2 hours.

The most challenging part was understanding how KMS permissions work separately from DynamoDB IAM permissions and troubleshooting the kms:Decrypt access error.

It was most rewarding to see encryption in action through a real access-denied and then access-granted scenario, clearly showing how KMS controls data security at rest.

I chose to do this project today because I wanted to understand how encryption works in real AWS services and see how KMS protects data in a practical setup with DynamoDB and IAM.

Something that would make learning with NextWork even better is more interactive troubleshooting scenarios and visual diagrams showing how data flows between IAM, KMS, and DynamoDB during encryption and decryption.

---

## Encryption and KMS

Encryption is the process of converting readable data (plaintext) into an unreadable format (ciphertext) using an algorithm so that only authorized users can decode it. Companies and developers do this to protect sensitive information like passwords, customer data, and financial records from unauthorized access. Encryption keys are digital codes used to lock (encrypt) and unlock (decrypt) the data.


AWS KMS (Key Management Service) is a managed cloud service that helps you create, store, and control encryption keys used to protect your data across AWS services. Key management systems are important because they ensure encryption keys are securely stored, properly controlled, and only accessible to authorized users, reducing the risk of data breaches and unauthorized access.


Encryption keys are broadly categorized as **symmetric and asymmetric keys**. Symmetric keys use a single shared key for both encryption and decryption, while asymmetric keys use a public-private key pair.

I set up a symmetric key because it is faster and more efficient for encrypting large amounts of data, which is ideal for securing a DynamoDB table in this project.


![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/aws-security-kms_a2b3c4d5)

---

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is stored at rest inside the table, ensuring that any data saved there is automatically encrypted using AWS KMS before it is written to disk and decrypted only when accessed with the proper permissions.


The different encryption options in DynamoDB include AWS owned keys, AWS managed keys (aws/dynamodb), and customer managed KMS keys.

Their differences are based on who controls the key and how much control and visibility you have over encryption management**.

I selected a customer managed KMS key because it gives the most control, including permissions, auditing, and key management.


![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/aws-security-kms_q8r9s0t1)

---

## Data Visibility

Rather than controlling who has access to the key, KMS manages user permissions by enforcing key policies and IAM permissions that define who can use the key and what actions they can perform (like encrypt or decrypt data).

Despite encrypting my DynamoDB table, I could still see the table’s items because I have permission to use the KMS key.

DynamoDB uses transparent data encryption, which means it automatically encrypts data at rest and decrypts it on demand for authorized users or applications, so the data appears readable while still being securely stored encrypted underneath.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/aws-security-kms_c0d1e2f3)

---

## Denying Access

I configured a new IAM user to test access to my DynamoDB table in a KMS-encrypted setup.

The permission policy I granted this user is AmazonDynamoDBFullAccess, but not any permissions to use the KMS key (AWS KMS access).

This setup lets me verify whether DynamoDB data can still be viewed without encryption key access.

After accessing the DynamoDB table as the test user, I encountered an Access Denied error for kms:Decrypt, because the user did not have permission to use the KMS key that encrypts the table.

This confirmed that even with full DynamoDB access, data cannot be viewed without KMS decryption permissions, proving that encryption and access control are enforced through AWS KMS.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/aws-security-kms_w0x1y2z3)

---

## EXTRA: Granting Access

To let my test user use the encryption key, I added nextwork-kms-user as a key user in the KMS key policy.

My key’s policy was updated to allow the test user to perform key usage actions such as Encrypt, Decrypt, ReEncrypt, GenerateDataKey, and DescribeKey, enabling them to access and decrypt data stored in the DynamoDB table.

Using the test user, I retried accessing the DynamoDB table after updating the KMS key policy. I observed that I could now successfully view the table items without errors.

This confirmed that granting KMS Decrypt permissions enabled the user to decrypt and read the encrypted data, showing that encryption access is enforced separately from DynamoDB permissions and depends on KMS authorization.

Encryption secures data instead of only controlling access to the service or resource itself.

I could combine encryption with IAM access control policies to add a second layer of security, ensuring that even if someone gains access to a resource, they still cannot read the data without the proper decryption permissions from KMS.

![Image](http://learn.nextwork.org/overjoyed_pink_zealous_snake/uploads/aws-security-kms_feffb2fb8)

---

---
