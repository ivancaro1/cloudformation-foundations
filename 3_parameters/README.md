# Parameters

Parameters are a way to provide inputs to your AWS CloudFormation template.
They are important to know about if:
  -  You want to reuse your templates across the company.
  -  Some inputs can not be determined ahead of time.

<img src="https://github.com/ivancaro1/cloudformation-foundations/assets/74940632/a2ab2ef9-3d7f-468c-9156-62b3325de13d"
 alt="Image Description" width="300"/>

## Parameters

Defines parameters that allow customization when deploying the CloudFormation stack.

- **SecurityGroupDescription:** Describes the purpose of the security group.
- **SecurityGroupPort:** Specifies a port range for the security group.
- **InstanceType:** Sets the type of EC2 instance with default and allowed values.
- **DBPwd:** Sets the password for the database admin account.
- **KeyName:** Specifies an existing EC2 KeyPair for SSH access to instances.
- **SecurityGroupIngressCIDR:** Defines the IP address range for EC2 instance communication.
- **MyVPC:** Specifies the VPC in which the resources will operate.
- **MySubnetIDs:** Provides a list of Subnet IDs.
- **DbSubnetIpBlocks:** Defines a comma-delimited list of CIDR blocks.

## Resources

Defines the AWS resources that will be created and configured by the CloudFormation stack.

### MyEC2Instance

- **Type:** AWS::EC2::Instance
- **Properties:** Configures an EC2 instance.

### MySecurityGroup

- **Type:** AWS::EC2::SecurityGroup
- **Properties:** Configures a security group for EC2 instances.

### DbSubnet1, DbSubnet2, DbSubnet3

- **Type:** AWS::EC2::Subnet
- **Properties:** Configures three subnets for the VPC.

