<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Miriangie Rondon  
**Email:** miriangier12@gmail.com

---

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate the concepts of policies and permissions especially in AWS where is very important who has access to what I'm doing this project to learn more about Cloud security and improve my skills in this key service offered by AWS.

### Tools and concepts

Services I used were EC2 AND IAM. The Key concepts I learnt include IAM users, IAM User groups, IAM Policies, Account Alias, AMI, Policy Simulators, how JSON policiees work, how to launch an instance, how to tag an instance.

### Project reflection

This project took approximately one hour to complete. The most challenging part was configuring the JSON IAM policy and ensuring that the permissions were correctly defined to enforce the intended access controls. The most rewarding part was validating the policy using the IAM Policy Simulator, which demonstrated how effective the tool is for testing and verifying permissions in a production environment.

---

## Tags

### What I did in this step

In this step, two Amazon EC2 instances are provisioned to scale the system’s compute resources. This improves the infrastructure’s ability to handle higher workloads, concurrent connections, and incoming requests while ensuring system reliability and performance.

### Understanding tags

Tags are key-value pairs assigned to AWS resources that help categorize and identify them. They are commonly used to organize resources, improve resource management, and make it easier to locate specific instances or services.

### My tag configuration

The tag I’ve used on my EC2 instances is called env The value I’ve assigned for my instances are production.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, a custom IAM policy is created to control access to the development EC2 instance. By applying the principle of least privilege, the policy ensures that users receive only the minimum permissions required to interact with the instance, reducing unnecessary access and improving overall security.

### Understanding IAM policies

AWS Identity and Access Management (IAM) policies are used to define and manage permissions within an AWS account. They specify what actions identities can perform on specific resources, making them a fundamental component of enforcing security and access control in AWS environments.

### The policy I set up

For this project, I’ve set up a policy using JSON so i can have a more granular control over the permissions.

### Policy effect

A custom IAM policy was implemented to provide controlled access to development EC2 instances while explicitly denying access to all other instances. The policy also prevents users from creating or deleting resource tags, ensuring tighter control over resource management and maintaining security boundaries.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource elements of an IAM JSON policy define how permissions are applied. Effect specifies whether an action is allowed or denied, Action defines which operations are permitted or restricted, and Resource identifies the AWS resources to which the policy applies.

---

## My JSON Policy

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will create an AWS account alias because I want to simplify user login.

### Understanding account aliases

An account alias is just an easier way to login and have access to your AWS Account! Instead of using a long AccountID, we can now refer our Account Alias instead.

### Setting up my account alias

Creating an account alias took me about 1 minute. Now, my new AWS console sign-in URL is https://nextwork-alias-miriangie.signin.aws.amazon.com/console


![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, an IAM group is created to manage access for all interns. Assigning permissions at the group level allows multiple users to inherit the same access policies, simplifying permission management and ensuring consistent access control across the team.

### Understanding user groups

IAM user groups are collections of users that share a common set of permissions. By attaching policies to the group, all users within the group inherit those permissions, simplifying access management and allowing administrators to control permissions more efficiently instead of managing users individually.

### Attaching policies to user groups

The custom IAM policy was attached to the IAM group, allowing all users in the group to inherit the defined permissions and access the development EC2 instances.

### Understanding IAM users

IAM users are individual identities created within an AWS account to represent people or services that require access to AWS resources. Each user can be assigned specific permissions to control what actions they are allowed to perform.

---

## Logging in as an IAM User

### Sharing sign-in details

Download the .csv file – AWS allows you to download a CSV file that contains the user’s sign-in credentials, including the username, password, and sign-in link. This file can then be securely shared with the user.

Copy the sign-in details manually – You can copy the username, password, and console sign-in URL directly from the AWS console and provide them to the user securely.

### Observations from the IAM user dashboard

After logging in as the IAM user, some actions resulted in an Access Denied message. This confirmed that the IAM policy correctly restricted permissions, preventing the user from performing actions that were not explicitly allowed.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, IAM configurations and user permissions are validated to confirm that the principle of least privilege is properly enforced and that users only have access to the resources necessary for their tasks.

### Testing policy actions

The JSON IAM policy was tested by attempting to stop both instances. Stopping the production EC2 instance resulted in an Access Denied response.

### Stopping the production instance

When attempting to stop the production EC2 instance, an Access Denied message appeared. This confirmed that the IAM policy is correctly enforcing permission restrictions and preventing unauthorized actions on production resources.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next I tried to stop the development EC2 instance which was successful. This confirms that the policy correctly enforces the intended permission boundaries.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to try a different way to test permissions. I'm doing this because the first time I tested it by stopping the instance which in a production environment can be very disruptive.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator allows administrators to evaluate IAM policies by simulating actions against AWS resources. This makes it possible to confirm whether specific actions will be allowed or denied without executing the actions in the environment.

### How I used the simulator

I set up a simulation for testing this policies and the results were denied. I had to adjust the settings and the result were allowed for stopping instances in the developement. 

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-security-iam_069d8a621)

---

---
