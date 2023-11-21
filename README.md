# AWS CloudFormation Foundations

Welcome to the AWS CloudFormation Foundations repository! This collection serves as a solid groundwork for deploying infrastructure on AWS using CloudFormation, enabling you to leverage Infrastructure as Code (IaC) principles.

## Overview

This repository includes:

- **Reusable Templates:** Foundational CloudFormation templates for common AWS services and configurations.
- **Best Practices:** Follows AWS best practices for secure, scalable, and efficient cloud infrastructure.

In every folder you can find a .md file that describes briefly what is the objective and the respective(s) YAML files. 

## What is CloudFormation

CloudFormation is a declarative way of outlining your AWS Infrastructure, for any resources. For example, within a CloudFormation template, you say:

- I want a security group
- I want two EC2 instances using this security group
- I want an S3 bucket.

### Benefits of using Cloud Formation

- **Infrastructure as code:** No resources are manually created, which is excellent for control. The code can be version-controlled for example using Git. Changes to the infrastructure are reviewed through code.
- **Cost:** Each resource within the stack is tagged with an identifier so you can easily how much a stack costs you. You can estimate the costs of your resources using the CloudFormation template.
- **Productivity:** Ability to destroy and re-create an infrastructure on the cloud on the fly. Automated generation of Diagrams for the templates.

## Getting Started

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/cloudformation-foundations.git

2. **VSCode Setup:** Install cfn-lint extension https://github.com/aws-cloudformation/cfn-lint
