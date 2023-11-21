## Resources

Resources are the core of your CloudFormation template.
They represent the different AWS Components that will be created and configured.
Resources are declared and can reference each other.

### Optional attributes for Resources
 - DependsOn: Very useful to draw a dependency between two resources.
 - DeletionPolicy: Protect resources from being deleted even if the CloudFormation stack is deleted.
 - UpdateReplacePolicy: Protect resources from being replaced during a CloudFormation update.

## DependsOn

### Parameters

Defines a parameter for the Amazon Machine Image (AMI) ID, with a default value pointing to the latest Amazon Linux AMI.

- **ImageId:**
  - **Type:** AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
  - **Default:** /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2

### Resources

Defines AWS resources, including an S3 bucket and an EC2 instance, with a dependency relationship.

- **MyS3Bucket:**
  - **Type:** AWS::S3::Bucket

- **MyInstance:**
  - **Type:** AWS::EC2::Instance
  - **Properties:**
    - **ImageId:** References the ImageId parameter.
    - **InstanceType:** t2.micro
  - **DependsOn:** Specifies that the EC2 instance creation depends on the creation of the MyS3Bucket.

### Summary

This CloudFormation template creates an S3 bucket and an EC2 instance. The instance's AMI ID is parameterized, and its creation depends on the successful creation of the S3 bucket. Adjust the parameters and resources as needed for your specific deployment.

## DeletionPolicy

### Resources

Defines an S3 bucket with a specified deletion policy.

- **MyS3Bucket:**
  - **Type:** AWS::S3::Bucket
  - **DeletionPolicy:** Retain

### Summary

This CloudFormation template creates an S3 bucket with a retention policy set to "Retain." The retention policy ensures that the S3 bucket and its contents are not deleted when the CloudFormation stack is deleted. Customize the template as needed for your specific use case.

## UpdateReplacePolicy

### Parameters

Defines a parameter for the S3 bucket name.

- **BucketName:**
  - **Type:** String

### Resources

Defines an S3 bucket with specified properties, a deletion policy, and an update replace policy.

- **MyS3Bucket:**
  - **Type:** AWS::S3::Bucket
  - **Properties:**
    - **BucketName:** References the BucketName parameter.
  - **DeletionPolicy:** Retain
  - **UpdateReplacePolicy:** Retain

### Summary

This CloudFormation template creates an S3 bucket with a retention policy set to "Retain" for both deletion and update operations. The bucket name is parameterized, allowing customization. Ensure to customize the template further based on your specific requirements.
