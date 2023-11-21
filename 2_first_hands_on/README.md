# Hands-On: Creating a S3 Bucket

Here we are going to create an S3 bucket. It's important to mention that creating a S3 bucket is completely free.
S3 is the AWS service for storing static files in a replicated and globally available way.

<img src="https://github.com/ivancaro1/cloudformation-foundations/assets/74940632/c265e463-1c11-477a-9439-94a9a8afa053"
 alt="Image Description" width="200"/>

## Resources Section

The template defines two resources: "MyS3Bucket" and "SomeS3AccessPolicy."

## AWS::S3::Bucket Type

- **MyS3Bucket:**
  - Creates an S3 bucket with configurable public access settings.
  
## AWS::S3::BucketPolicy Type

- **SomeS3AccessPolicy:**
  - Establishes a bucket policy granting public read access to the contents of "MyS3Bucket."

## Properties

### Public Access Settings (MyS3Bucket):

- **BlockPublicAcls:** Allows or blocks ACLs that are public.
- **BlockPublicPolicy:** Allows or blocks public policies for the bucket.
- **IgnorePublicAcls:** Specifies whether to ignore public ACLs.
- **RestrictPublicBuckets:** Specifies whether to restrict access to buckets with public policies.

### Bucket Policy (SomeS3AccessPolicy):

- Grants public read access to the contents of the bucket.
- Uses the `Fn::Sub` function to dynamically substitute the bucket name in the policy.

## Usage Instructions

1. Copy the CloudFormation template above.
2. Open the AWS Management Console.
3. Navigate to the CloudFormation service.
4. Create a new stack and paste the template.
5. Follow the wizard to customize and deploy your resources.

Feel free to modify and extend the template according to your specific requirements. For more information, refer to the [AWS CloudFormation documentation](https://docs.aws.amazon.com/cloudformation/).

