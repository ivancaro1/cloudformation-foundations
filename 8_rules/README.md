# Rules

Rules used to perform parameter validations based on the values of other parameters (cross-parameter validation)

<img src="https://github.com/ivancaro1/cloudformation-foundations/assets/74940632/2f87b5f5-5bb0-402e-87c1-c4ba13ce6c0a"
 alt="Image Description" width="500"/>

 ## How to define a Rule?

 Each Rule consists of:

 - Rule Condition (optional): determines when a rule takes effect/assertions applied (only one per rule)
 - Assertions: describes what values are allowed for a particular parameter.

## Parameters

Defines parameters for the EC2 instance type, environment, and Amazon Machine Image (AMI) ID.

- **InstanceType:**
  - **Type:** String
  - **Default:** t2.small
  - **AllowedValues:** [t2.nano, t2.micro, t2.small]

- **Environment:**
  - **Type:** String
  - **Default:** dev
  - **AllowedValues:** [dev, prod]

- **ImageId:**
  - **Type:** AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
  - **Default:** /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2

## Rules

Defines rules for validating instance type based on the specified environment.

- **ProdInstanceType:**
  - **RuleCondition:** Checks if the environment is prod.
  - **Assertions:**
    - Checks if the instance type is t2.small for a production environment.

- **DevInstanceType:**
  - **RuleCondition:** Checks if the environment is dev.
  - **Assertions:**
    - Checks if the instance type is t2.nano or t2.micro for a development environment.

## Resources

Defines an EC2 instance resource with specified properties.

- **MyEC2Instance:**
  - **Type:** AWS::EC2::Instance
  - **Properties:**
    - **InstanceType:** References the InstanceType parameter.
    - **ImageId:** References the ImageId parameter.

## Summary

This CloudFormation template creates an EC2 instance with validation rules based on the specified environment. Rules ensure that the instance type aligns with the environment type. Customize the parameters and rules as needed for your specific deployment.
