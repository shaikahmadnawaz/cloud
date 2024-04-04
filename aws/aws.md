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

![IAM Architecture](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/iam.png)

### Overview

IAM allows you to create and manage users and groups, assign permissions using policies, and set up roles for cross-account access. By using IAM, you can ensure that only authorized users and applications have access to your AWS resources, enhancing security and compliance.

### Key Concepts

- **Users**: IAM users are entities with unique security credentials that can be used to access AWS services.
- **Groups**: IAM groups are collections of users, making it easier to manage permissions for multiple users with similar access requirements.
- **Roles**: IAM roles are sets of permissions that can be assumed by users, applications, or services within your AWS account.
- **Policies**: IAM policies are JSON documents that define permissions and access control rules for users, groups, and roles.
- **Access Keys**: IAM access keys consist of an access key ID and secret access key, which are used to authenticate requests made programmatically to AWS services.
- **Multi-factor Authentication (MFA)**: IAM supports multi-factor authentication for an extra layer of security when accessing AWS resources.

### Benefits

- **Granular Control**: IAM provides granular control over who can access specific AWS resources and what actions they can perform.
- **Security**: IAM helps you enforce least privilege principles by granting only the permissions necessary for users to perform their tasks.
- **Compliance**: IAM supports compliance requirements by enabling you to enforce access controls, audit access, and generate access reports.
- **Integration**: IAM integrates with other AWS services, allowing you to secure resources across your entire AWS environment.

### Getting Started

![IAM Architecture](https://cloud-learning-content.s3.ap-south-1.amazonaws.com/iam-dashboard.png)

To get started with IAM, you can access the IAM console through the AWS Management Console. From there, you can create IAM users, groups, roles, and policies, and assign permissions as needed.

### Conclusion

AWS Identity and Access Management (IAM) is a crucial component of securing your AWS environment. By using IAM, you can manage access to AWS services and resources effectively, ensuring that only authorized entities have access while maintaining security and compliance standards.
