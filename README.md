# Terraform-aws-ecr

# AWS Infrastructure Provisioning with Terraform

## Table of Contents
- [Introduction](#introduction)
- [Usage](#usage)
- [Module Inputs](#module-inputs)
- [Module Outputs](#module-outputs)
- [License](#license)

## Introduction
This module is basically combination of Terraform open source and includes automatation tests and examples. It also helps to create and improve your infrastructure with minimalistic code instead of maintaining the whole infrastructure code yourself.

## Usage
To use this module, you can include it in your Terraform configuration. Here's an example of how to use it:

## Examples

## Example: private_ecr

```hcl
module "private_ecr" {
  source             = "git::https://github.com/cypik/terraform-aws-ecr.git?ref=v1.0.0"
  enable_private_ecr = true
  name               = local.name
  environment        = local.environment
  scan_on_push       = true
  max_image_count    = 7
}
```

## Example: public_ecr
```hcl
module "public_ecr" {
  source                   = "git::https://github.com/cypik/terraform-aws-ecr.git?ref=v1.0.0"
  enable_public_ecr        = true
  name                     = local.name
  environment              = local.environment
  max_untagged_image_count = 1
  max_image_count          = 7
  public_repository_catalog_data = {
    description       = "Docker container for some things"
    operating_systems = ["Linux"]
    architectures     = ["x86"]
  }
}
```

## Module Inputs
- `name`:  (Required) Name of the repository.
- `scan_on_push`: (Required) Indicates whether images are scanned after being pushed to the repository (true) or not scanned (false).
- `subject_alternative_names`: Set of domains that should be SANs in the issued certificate.

- For security group settings, you can configure the ingress and egress rules using variables like:

## Module Outputs
- `id` : The repository name.
- `arn` : Full ARN of the repository.
- `registry_id`: The registry ID where the repository was created.
- `tags` : (Optional) A map of tags to assign to the resource.

- Other relevant security group outputs (modify as needed).

## Example
For detailed examples on how to use this module, please refer to the '[example](https://github.com/cypik/terraform-aws-ecr/blob/master/example)' directory within this repository.

## Author
Your Name Replace '[License Name]' and '[Your Name]' with the appropriate license and your information. Feel free to expand this README with additional details or usage instructions as needed for your specific use case.

## License
This project is licensed under the MIT License - see the [LICENSE](https://github.com/cypik/terraform-aws-ecr/blob/master/LICENSE) file for details.