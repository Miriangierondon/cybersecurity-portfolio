<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Miriangie Rondon  
**Email:** miriangier12@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

In this project, I will demonstrate how cloud networking works, i'm doing this project to learn  how to create a VPC and how cloud infrastructure really works.

### What is Amazon VPC?

Amazon VPC is a service that allows you to create a logically isolated network within AWS. It enables you to define your own networking environment, giving you control over how resources are organized, secured, and managed within that private space.

In today’s project, I used Amazon VPC to create a Virtual Private Cloud, configure subnets, and set up an Internet Gateway to enable network connectivity.

### Personal reflection

This project took me about 30 minutes and provided valuable hands-on experience with AWS networking, helping me better understand how its components function in practice.

One thing I didn’t expect in this project was how eye-opening it would be. It gave me a deeper understanding of VPCs and how networking operates within AWS, allowing me to see more clearly how resources are structured and communicate in the cloud.

---

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I willl access the VPC console and create a VPC because I want to build a VPC and demostrate how the networking behind it works.

### How VPCs work

VPCs are like a smaller, more secure space where your resources are easier to manage. Without this, there would be no privacy, and everyone would have access and be able to see your resources.

### Why there is a default VPC in AWS accounts

A default VPC was already available in my account when my AWS account was created. AWS provides this default VPC so users can start using resources without having to create one themselves, which makes it especially helpful for beginners.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To configure the VPC, an IPv4 CIDR block of 10.0.0.0/16 was defined. This CIDR allocation establishes the network and host address portions, determines the total addressable IP range within the VPC, and governs how the address space can be segmented into subnets and allocated to resource

---

## Subnets

### What I did in this step

In this step, I will configure a subnet within the VPC to enable more granular control over resource allocation and network segmentation. This allows for better traffic management, reduced congestion, and improved organization of how resources operate and communicate with one another within the network.

### Creating and configuring subnets

Subnets are smaller, logically segmented networks within a VPC that allow you to organize and isolate resources at a more granular level. They enable better control over IP address allocation, traffic flow, and security policies within the overall network. By default, AWS provides preconfigured subnets in a default VPC, typically with one subnet per Availability Zone (AZ) in the selected region. This design supports high availability and fault tolerance by allowing resources to be distributed across multiple AZs. These default subnets also come with basic configurations that allow resources launched within them to communicate with the internet, making them convenient for initial deployments and testing environments.

### Public vs private subnets

The key difference between public and private subnets lies in their internet accessibility and intended use. Public subnets are configured to allow direct communication with the internet, typically used for resources such as web servers that require external access. In contrast, private subnets are designed for internal operations and host resources that should not be exposed to the internet, such as databases or backend services, allowing communication only within the private network. For a subnet to be classified as public, it must have a route to an Internet Gateway, enabling inbound and outbound internet connectivity.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

After creating the subnet, I enabled the auto-assign public IPv4 setting. This configuration ensures that resources launched within the subnet are automatically assigned a public IP address, eliminating the need for manual allocation. This streamlines the deployment process and improves efficiency by reducing additional configuration steps.

---

## Internet gateways

### What I did in this step

In this step, I will create an Internet Gateway, which enables connectivity between the VPC and the internet. This component allows resources within the VPC, particularly those in public subnets, to send and receive traffic from external networks.

### Setting up internet gateways

An Internet Gateway serves as the connection point between a VPC and the public internet, enabling resources to send and receive traffic to and from external users, servers, and networks.

Attaching an Internet Gateway to a VPC enables internet connectivity for resources within that network. Without this step, resources would not be able to communicate with or be accessed from the public internet, making them unreachable externally.

![Image](http://learn.nextwork.org/secure_purple_noble_pufferfish/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

### What I'm doing in this extension

### Exploring CloudShell and CLI

### Debugging my setup

### Comparing CloudShell vs AWS Console

---

---
