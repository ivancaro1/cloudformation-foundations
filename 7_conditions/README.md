# Introduction

Here we are goint to create a simple EC2 instance, and we are going to add security group to it

<img src="https://github.com/ivancaro1/cloudformation-foundations/assets/74940632/77f42400-196d-48e4-9ef3-79983ebc1378" alt="Image Description" width="200"/>

## Resources Section

The template defines a resource named "MyInstance."

## AWS::EC2::Instance Type

Specifies that the resource is an EC2 instance, which is a virtual server in AWS.

## Properties

Describes the configuration of the EC2 instance.

### AvailabilityZone

Sets the availability zone for the EC2 instance to "us-east-1a." An availability zone is a data center within an AWS region.

### ImageId

Specifies the Amazon Machine Image (AMI) ID, which is a pre-configured virtual machine image. In this case, it uses the AMI with ID "ami-0742b4e673072066f."

### InstanceType

Sets the type of EC2 instance to "t2.micro." This determines the computing capacity and performance characteristics of the instance.

## Summary

In summary, this CloudFormation template is a basic blueprint for creating a small t2.micro EC2 instance in the specified AWS region (us-east-1a) using a specific AMI. You can customize the template to include additional configurations and resources based on your needs.
