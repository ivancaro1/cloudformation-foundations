# Nested

Nested stacks are stacks as part of other stacks.
They allow us to isolate repeated patterns/common components in separate stacks and call them from other stacks.
Nested stacks are considered best practice.

<img src="https://github.com/ivancaro1/cloudformation-foundations/assets/74940632/f60413b0-e863-4b78-b6aa-c32ab327a98e"
 alt="Image Description" width="500"/>

## Parameters

Defines parameters for the application name and VPC ID.

- **ApplicationName:**
  - **Description:** The application name
  - **Type:** String

- **VPCId:**
  - **Description:** VPC to create the security group info
  - **Type:** AWS::EC2::VPC::Id

## Resources

Defines an EC2 security group resource with specific ingress rules based on IP ranges.

- **SSHSecurityGroup:**
  - **Type:** AWS::EC2::SecurityGroup
  - **Properties:**
    - **GroupDescription:** Describes the security group for the specified application.
    - **SecurityGroupIngress:**
      - Allows SSH access from IP range "10.0.0.0/25" with a description for the Engineering department.
      - Allows SSH access from IP range "192.168.0.0/25" with a description for the HR department.
    - **VpcId:** References the VPCId parameter.

## Outputs

Defines an output for the SSH security group ID.

- **SSHGroupId:**
  - **Value:** References the SSHSecurityGroup resource.
  - **Description:** ID for the SSH Security Group

## Summary

This CloudFormation template creates an EC2 security group with specific SSH ingress rules for different departments within the specified VPC. The template also exports the SSH security group ID for potential use in other stacks or resources. Customize the parameters and resources as needed for your specific deployment.
