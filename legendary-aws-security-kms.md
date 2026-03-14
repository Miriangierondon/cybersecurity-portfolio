<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Encrypt Data with AWS KMS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-kms)

**Author:** Miriangie Rondon  
**Email:** miriangier12@gmail.com

---

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-kms_w0x1y2z3)

---

## Introducing Today's Project!

In this project, I will demonstrate the importance of integrity and security in the modern digital world. The goal is to explore how we can protect valuable resources—especially those stored in the cloud—by using security techniques such as encryption. Through this analysis, the project highlights how encryption works and why it plays a critical role in keeping data safe and trustworthy.

### Tools and concepts

The services used in this project include AWS Identity and Access Management (IAM), AWS Key Management Service (KMS), and Amazon DynamoDB. These services were used to demonstrate how encryption and access control mechanisms work together to protect data stored in cloud resources.

Throughout this project, several key concepts were explored, including encryption, KMS key policies, DynamoDB tables and items, symmetric and asymmetric encryption, transparent data encryption, IAM roles, and access control mechanisms. Additional concepts included different types of encryption keys such as customer managed keys, AWS managed keys, and AWS owned keys, as well as the different states of data protection: data at rest, data in transit, and data in use. These concepts helped illustrate how AWS services can be combined to secure data and control access effectively.

### Project reflection

This project took approximately one hour to complete. One of the most rewarding aspects was observing the AWS KMS key in action, particularly how it encrypted and decrypted the data based on different permission configurations. This demonstrated how encryption and access control work together to protect sensitive data and ensure that only authorized users can access or decrypt it.

I chose to complete this project today because encryption is a fundamental component of the modern digital world and plays a critical role in how data is protected and transmitted. Understanding how encryption works is essential for securing information and building reliable systems. As for improving the learning experience with NextWork, I believe the platform already provides an excellent learning environment and I would not suggest any changes at this time.

---

## Encryption and KMS

Encryption is the process of protecting data by converting readable information, known as plaintext, into an unreadable format called ciphertext. This process uses cryptographic algorithms to transform the data so that it cannot be understood by unauthorized users. The purpose of encryption is to protect sensitive information and help maintain the confidentiality and integrity of data.

Organizations and developers use encryption to ensure that data remains secure both during storage and transmission. By encrypting data, only authorized parties with the proper credentials are able to access and interpret the information, preventing unauthorized individuals from viewing or modifying it.

Encryption keys are secret values used together with cryptographic algorithms to determine how the data will be encrypted and later decrypted. The algorithm defines the method used for encryption, while the key controls the specific transformation applied to the data.

AWS Key Management Service (KMS) is a managed service provided by Amazon Web Services that allows organizations to create, manage, and control cryptographic keys used to protect their data. A key management system is important because it securely stores and manages encryption keys while controlling who can use them and how they are used.

AWS KMS helps organizations protect sensitive information by ensuring that encryption keys are generated, stored, and used in a secure environment. It also provides features such as access control, auditing, and automatic key rotation to help maintain strong security practices and protect keys from unauthorized access or potential attacks.

Encryption keys are broadly categorized into symmetric keys and asymmetric keys. Symmetric encryption uses a single key for both encryption and decryption, meaning the same key is used to convert plaintext into ciphertext and to convert the ciphertext back into plaintext. In contrast, asymmetric encryption uses two different keys, a public key and a private key, where one key is used for encryption and the other is used for decryption.

For this setup, a symmetric key was created because the encryption and decryption operations will be performed using the same key. Symmetric keys are commonly used when high performance and efficiency are required for encrypting and decrypting data.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-kms_a2b3c4d5)

---

## Encrypting Data

My encryption key will be used to safeguard data stored in Amazon DynamoDB, one of Amazon Web Services' managed database services. DynamoDB is a fully managed NoSQL database known for its high performance, scalability, and ease of use. By integrating DynamoDB with AWS Key Management Service (KMS), data stored in the table can be encrypted at rest, ensuring that sensitive information remains protected from unauthorized access.

Amazon DynamoDB provides several encryption options for protecting data at rest. These options include encryption owned by Amazon DynamoDB, encryption using an AWS managed key, and encryption using a customer managed key stored in your AWS account. The main difference between these options is the level of control and management you have over the encryption key.

Encryption owned by Amazon DynamoDB is fully managed by AWS and requires no configuration from the user. Encryption using an AWS managed key allows AWS to manage the key on behalf of the customer while still enabling integration with AWS services. The third option, a customer managed key stored in your account, allows you to create and manage the key yourself using AWS Key Management Service (KMS).

For this project, the option stored in your account and owned and managed by you was selected because the encryption key was created and managed directly in AWS KMS. This option provides greater control over key.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-kms_q8r9s0t1)

---

## Data Visibility

Rather than controlling access through standard resource permissions alone, AWS Key Management Service (KMS) manages user permissions through key policies, IAM policies, and grants.

Key policies are the primary way to control access to a KMS key. They define which users, roles, or AWS services are allowed to use or manage the key. In addition to key policies, IAM policies can be used to grant permissions for specific actions such as encrypting, decrypting, or describing a key. KMS also supports grants, which allow temporary or service-specific permissions to use a key without modifying the key policy.

Together, these mechanisms ensure that only authorized users or services can perform cryptographic operations with the KMS key, helping maintain strong security and control over encrypted data.

Even though the DynamoDB table is encrypted, I was still able to view the table’s items. This is because Amazon DynamoDB uses transparent data encryption. Transparent encryption means that the encryption and decryption process happens automatically in the background.

Since I have the appropriate permissions to access the table, DynamoDB automatically decrypts the data when it is retrieved. The encryption protects the data at rest, meaning it remains encrypted while stored in the database. However, authorized users and applications can still read the data normally because the service decrypts it transparently when it is accessed.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-kms_c0d1e2f3)

---

## Denying Access

I configured a new IAM user to serve as a test user in order to evaluate the effectiveness of the AWS KMS key configuration. This user was granted the AmazonDynamoDBFullAccess permission policy, allowing them to interact with DynamoDB resources. However, the user was not granted permission to use the KMS key responsible for encrypting the data.

Because the user does not have the required permissions defined in the KMS key policy, they are unable to decrypt or access the encrypted values protected by the key. This setup demonstrates how KMS key policies and IAM permissions work together to control access to encrypted data, ensuring that only authorized users can decrypt and retrieve sensitive information.

After accessing the DynamoDB table as the test user, an error message was encountered because the user did not have the necessary permissions to use the KMS key associated with the encrypted table. Although the user had permission to access DynamoDB, they were not authorized to decrypt the data protected by the key. This confirmed that the KMS encryption and access controls are working as intended, since only users with the appropriate KMS permissions are able to access the encrypted data.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-kms_w0x1y2z3)

---

## EXTRA: Granting Access

To allow the test user to use the encryption key, the user was added as a key user in the KMS key configuration. This update granted the test user permission to perform cryptographic operations with the key. As part of this change, the KMS key policy was modified to allow the test user to perform actions such as Encrypt, Decrypt, ReEncrypt, GenerateDataKey, and DescribeKey. These permissions enable the user to interact with the encrypted data while still maintaining controlled access through the key policy.

Using the test user, I attempted to access the encrypted value again. This time, the data was successfully retrieved, confirming that the KMS key permissions had been correctly configured. The successful retrieval demonstrates that the encryption mechanism and access controls are functioning as intended, allowing authorized users to decrypt and access the protected data.

Encryption protects the data itself, not the entire service where the data is stored. While encryption ensures that sensitive information remains unreadable to unauthorized users, additional security mechanisms are required to control access to the service. For example, encryption can be combined with security groups, IAM policies, or resource policies to manage who can access the service and interact with its resources. By combining these controls, organizations can protect both the infrastructure and the data stored within it, ensuring a stronger overall security posture.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-kms_feffb2fb8)

---

---
