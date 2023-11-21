# Conditions

Conditions are used to control the creation of resources or outputs based on a condition.
Conditions can be whaterver you want them to be, but common ones are:
-  Environment (dev/test/prod)
-  AWS Region
-  Any parameter value
Each condition can reference another condition, parameter value or mapping.

<img src="https://github.com/ivancaro1/cloudformation-foundations/assets/74940632/9c020877-9019-4d1b-8a3b-a4a7f9b2fd36"
 alt="Image Description" width="400"/>

## How to define a condition?

The intrinsic function (logical) can be any of the following:
- Fn::And
- Fn::Equals
- Fn::If
- Fn::Not
- Fn::Or

## Fn::GetAtt
Attributes are attached to any resources you create.

## Parameters

Defines parameters for the Amazon Machine Image (AMI) ID and environment type.

- **ImageId:**
  - **Type:** AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
  - **Default:** /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2

- **EnvType:**
  - **Description:** Environment type.
  - **Default:** test
  - **Type:** String
  - **AllowedValues:** [prod, test]
  - **ConstraintDescription:** must specify prod or test.

## Conditions

Defines a condition based on the environment type.

- **CreateProdResources:**
  - Checks if EnvType is set to prod.

## Resources

Defines AWS resources, including an EC2 instance, volume attachment, and volume, with conditions applied.

- **EC2Instance:**
  - **Type:** AWS::EC2::Instance
  - **Properties:**
    - **ImageId:** References the ImageId parameter.
    - **InstanceType:** t2.micro

- **MountPoint:**
  - **Type:** AWS::EC2::VolumeAttachment
  - **Condition:** CreateProdResources
  - **Properties:**
    - **VolumeId:** References the NewVolume resource.
    - **InstanceId:** References the EC2Instance resource.
    - **Device:** /dev/sdh

- **NewVolume:**
  - **Type:** AWS::EC2::Volume
  - **Condition:** CreateProdResources
  - **Properties:**
    - **Size:** 100
    - **AvailabilityZone:** Retrieves the availability zone from the EC2Instance.

## Outputs

Defines an output for the volume ID, conditionally applied based on the environment type.

- **VolumeId:**
  - **Condition:** CreateProdResources
  - **Value:** References the NewVolume resource.
