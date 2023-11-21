## Parameters

Defines a parameter to specify the environment name.

- **EnvironmentName:**
  - **Description:** Environment Name
  - **Type:** String
  - **AllowedValues:** [development, production]
  - **ConstraintDescription:** must be development or production

## Mappings

Mappings are fixed variables within your CloudFormation template.
They are very andy to differentiate between different environments (dev vs prod), regions (AWS regions), AMI types, etc.
All the values are hardcoded within the template.

Maps AWS region and architecture to Amazon Machine Images (AMIs) and environment names to instance types.

- **AWSRegionArch2AMI:**
  - Maps AWS region and architecture to AMIs.

- **EnvironmentToInstanceType:**
  - Maps environment names to EC2 instance types.

## Resources

Defines an EC2 instance resource using the specified parameters and mappings.

- **EC2Instance:**
  - **Type:** AWS::EC2::Instance
  - **Properties:**
    - **InstanceType:** Uses the instance type mapped based on the environment name.
    - **ImageId:** Uses the AMI mapped based on the AWS region and architecture.

## Summary

This CloudFormation template allows you to deploy an EC2 instance with a specified instance type and AMI based on the environment name, AWS region, and architecture. Customize the parameters and mappings as needed for your specific deployment.
