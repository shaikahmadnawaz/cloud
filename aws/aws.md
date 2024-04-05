# Amazon Web Services (AWS)

- An Amazon subsidiary that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments.
- Offers a wide range of services, including computing power, storage, databases, machine learning, analytics, and more.
- Provides a pay-as-you-go pricing model, allowing users to pay only for the services they use.

## AWS Charges

- AWS charges users based on their usage of services, such as compute instances, storage, data transfer, and other resources.
- Pricing models include on-demand, reserved instances, and spot instances, each with different cost structures and benefits.
- The AWS Free Tier offers limited free usage of select services for new customers to explore and experiment with AWS.
- Users can set up billing alerts and budgets to manage costs and avoid unexpected charges.

## AWS Global Infrastructure

![AWS Global Infrastructure](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/regions-azs.png)

- AWS Region - A physical location in the world where AWS data centers. Each region consists of multiple availability zones.
- AWS Availability Zone - One or more discrete data centers with redundant power, networking, and connectivity within a region.

- AWS operates in multiple geographic regions around the world, each consisting of multiple availability zones.
- Availability zones are distinct locations within a region that are engineered to be isolated from failures in other zones.
- Edge locations are endpoints for AWS services that are used for caching content and reducing latency for end-users.
- AWS Regions and Availability Zones are interconnected through a high-speed network to provide low-latency and high-availability services.

## AWS Shared Responsibility Model

![AWS Shared Responsibility Model](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/Shared_Responsibility_Model_V2.jpg)

- AWS operates on a shared responsibility model, where AWS is responsible for the security of the cloud infrastructure, and customers are responsible for securing their data and applications.
- AWS provides security of the cloud, including physical security, network security, and infrastructure security.
- Customers are responsible for security in the cloud, including data encryption, access control, and compliance with security best practices.
- AWS offers a wide range of security services and features to help customers secure their workloads on the AWS cloud.
- Customers can use AWS Identity and Access Management (IAM) to manage user access and permissions to AWS services and resources.
- AWS provides compliance certifications and reports to help customers meet regulatory requirements and industry standards.
- Customers can use AWS CloudTrail to monitor and log AWS account activity for security and compliance purposes.
- AWS offers a shared responsibility model for managing security in the cloud, ensuring that both AWS and customers play a role in securing workloads on the AWS platform.

## AWS Identity and Access Management (IAM)

AWS Identity and Access Management (IAM) is a web service that enables you to securely control access to AWS services and resources. It helps you manage users, groups, roles, and permissions within your AWS account.

![AWS IAM Architecture](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/iam-arc.png)

### IAM Overview

IAM allows you to create and manage users and groups, assign permissions using policies, and set up roles for cross-account access. By using IAM, you can ensure that only authorized users and applications have access to your AWS resources, enhancing security and compliance.

### IAM Key Concepts

- **Users**: IAM users are entities with unique security credentials that can be used to access AWS services.
- **Groups**: IAM groups are collections of users, making it easier to manage permissions for multiple users with similar access requirements.
- **Roles**: IAM roles are sets of permissions that can be assumed by users, applications, or services within your AWS account.
- **Policies**: IAM policies are JSON documents that define permissions and access control rules for users, groups, and roles.
- **Access Keys**: IAM access keys consist of an access key ID and secret access key, which are used to authenticate requests made programmatically to AWS services.
- **Multi-factor Authentication (MFA)**: IAM supports multi-factor authentication for an extra layer of security when accessing AWS resources.

### IAM Benefits

- **Granular Control**: IAM provides granular control over who can access specific AWS resources and what actions they can perform.
- **Security**: IAM helps you enforce least privilege principles by granting only the permissions necessary for users to perform their tasks.
- **Compliance**: IAM supports compliance requirements by enabling you to enforce access controls, audit access, and generate access reports.
- **Integration**: IAM integrates with other AWS services, allowing you to secure resources across your entire AWS environment.

### Getting Started with IAM

![IAM dashboard](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/iam-dashboard.png)

To get started with IAM, you can access the IAM console through the AWS Management Console. From there, you can create IAM users, groups, roles, and policies, and assign permissions as needed.

### IAM Resources

- [IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/)
- [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [IAM FAQs](https://aws.amazon.com/iam/faqs/)

## Elastic Compute Cloud (EC2) Overview

Elastic Compute Cloud (EC2) is a web service that provides resizable compute capacity in the cloud. It enables users to launch and manage virtual servers, known as instances, to run applications and workloads.

### Key Components

- **Processor**: EC2 instances utilize virtualized CPUs (Central Processing Units) with various performance capabilities to handle computational tasks efficiently.
- **Memory**: EC2 instances come with different memory sizes, allowing users to choose the appropriate amount of RAM (Random Access Memory) for their applications.
- **Hard Disk or SSD**: EC2 instances offer storage options ranging from traditional hard disk drives (HDDs) to high-performance solid-state drives (SSDs) for storing data and operating system images.
- **Network Interface Card (NIC)**: Each EC2 instance is equipped with one or more network interfaces to facilitate communication with other instances and external networks.
- **Network Switch or Router**: AWS's network infrastructure includes switches and routers that route traffic between EC2 instances and other AWS services.

### Virtualization

![EC2 Virtualization](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/virtualisation.png)

EC2 instances are built on top of virtualization technology, facilitated by a software component known as a hypervisor. The hypervisor creates and manages virtual machines (VMs), allowing multiple EC2 instances to run on a single physical server. This enables efficient resource utilization and isolation between instances, ensuring security and performance.

#### Hypervisor

A hypervisor, also known as a virtual machine monitor (VMM), is responsible for abstracting physical hardware resources and creating virtualized environments, known as VMs. There are two main types of hypervisors:

1. **Type 1 Hypervisor (Bare Metal)**: This hypervisor runs directly on the physical hardware without the need for an underlying operating system. It provides better performance and security compared to Type 2 hypervisors.

2. **Type 2 Hypervisor (Hosted)**: This hypervisor runs on top of an existing operating system. It is typically used for development and testing environments but may introduce some overhead due to the underlying OS.

### Instance Types

EC2 offers a variety of instance types optimized for different use cases, such as general-purpose, compute-optimized, memory-optimized, storage-optimized, and accelerated computing instances. Each instance type is designed to deliver specific performance characteristics to meet the needs of various workloads.

### Amazon Machine Images (AMIs)

Amazon Machine Images (AMIs) are pre-configured templates that contain the operating system, software, and configurations required to launch an EC2 instance. Users can choose from a wide range of public AMIs provided by AWS or create custom AMIs tailored to their specific requirements.

### EC2 User Data

EC2 user data allows users to run scripts or commands when launching EC2 instances. This feature enables automated configuration and setup tasks, such as installing software, configuring settings, and initializing data. User data can be provided during instance launch via the AWS Management Console, API, or CLI.

### EC2 Metadata

EC2 metadata provides information about an instance's configuration and environment, such as instance ID, instance type, public IP address, and security groups. Metadata can be accessed from within the instance using a special URL ([http://169.254.169.254/latest/meta-data/](http://169.254.169.254/latest/meta-data/)) and is commonly used by applications and scripts to retrieve instance-specific information dynamically.

### EC2 Overview

EC2 offers a wide selection of instance types with varying compute, memory, storage, and networking capabilities, allowing users to choose the most suitable configuration for their workload requirements. EC2 instances can be easily launched, stopped, terminated, and resized as needed, providing flexibility and scalability.

### EC2 Benefits

- **Scalability**: EC2 enables you to scale compute capacity up or down based on demand, ensuring optimal performance and cost-efficiency.
- **Flexibility**: With a wide selection of instance types and configurations, EC2 offers flexibility to meet diverse workload requirements.
- **Reliability**: EC2 instances are built on AWS's highly reliable infrastructure, providing high availability and fault tolerance.
- **Security**: EC2 instances can be secured using security groups, key pairs, and other security measures to protect against unauthorized access and security threats.

### Getting Started with EC2

To get started with EC2, you can launch instances using the AWS Management Console, AWS Command Line Interface (CLI), or AWS Software Development Kits (SDKs). You can choose an AMI, select an instance type, configure security settings, and launch the instance within minutes.

![EC2 Dashboard](<https://cloud-learning-content.s3.ap-south-1.amazonaws.com/Screenshot+(1814).png>)

Configuration of EC2 instance:

![EC2 Configuration](<https://cloud-learning-content.s3.ap-south-1.amazonaws.com/Screenshot+(1816).png>)

Instances launched:

![All instances](<https://cloud-learning-content.s3.ap-south-1.amazonaws.com/Screenshot+(1817).png>)

Connect to the instance:

![Connect to instance](<https://cloud-learning-content.s3.ap-south-1.amazonaws.com/Screenshot+(1819).png>)

Terminate the instance:

![Terminate instance](<https://cloud-learning-content.s3.ap-south-1.amazonaws.com/Screenshot+(1820).png>)

### EC2 Resources

- [EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/)
- [EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)
- [EC2 Pricing](https://aws.amazon.com/ec2/pricing/)
- [EC2 FAQs](https://aws.amazon.com/ec2/faqs/)

Explore the EC2 documentation and resources to learn more about how to leverage EC2 instances for your computing needs in the cloud.
