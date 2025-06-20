---
subcategory: "Verified Access"
layout: "aws"
page_title: "AWS: aws_verifiedaccess_instance"
description: |-
  Terraform resource for managing a Verified Access Instance.
---

# Resource: aws_verifiedaccess_instance

Terraform resource for managing a Verified Access Instance.

## Example Usage

### Basic

```terraform
resource "aws_verifiedaccess_instance" "example" {
  description = "example"

  tags = {
    Name = "example"
  }
}
```

### With `fips_enabled`

```terraform
resource "aws_verifiedaccess_instance" "example" {
  fips_enabled = true
}
```

### With `cidr_endpoints_custom_subdomain`

```terraform
resource "aws_verifiedaccess_instance" "example" {
  cidr_endpoints_custom_subdomain = "test.example.com"
}
```

## Argument Reference

The following arguments are optional:

* `region` - (Optional) Region where this resource will be [managed](https://docs.aws.amazon.com/general/latest/gr/rande.html#regional-endpoints). Defaults to the Region set in the [provider configuration](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#aws-configuration-reference).
* `description` - (Optional) A description for the AWS Verified Access Instance.
* `fips_enabled` - (Optional, Forces new resource) Enable or disable support for Federal Information Processing Standards (FIPS) on the AWS Verified Access Instance.
* `cidr_endpoints_custom_subdomain` - (Optional) The custom subdomain for the CIDR endpoints.
* `tags` - (Optional) Key-value mapping of resource tags. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `creation_time` - The time that the Verified Access Instance was created.
* `id` - The ID of the AWS Verified Access Instance.
* `last_updated_time` - The time that the Verified Access Instance was last updated.
* `verified_access_trust_providers` - One or more blocks of providing information about the AWS Verified Access Trust Providers. See [verified_access_trust_providers](#verified_access_trust_providers) below for details.One or more blocks

### verified_access_trust_providers

Each `verified_access_trust_providers` supports the following argument:

* `description` - The description of trust provider.
* `device_trust_provider_type` - The type of device-based trust provider.
* `trust_provider_type` - The type of trust provider (user- or device-based).
* `user_trust_provider_type` - The type of user-based trust provider.
* `verified_access_trust_provider_id` - The ID of the trust provider.

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import Verified Access Instances using the `id`. For example:

```terraform
import {
  to = aws_verifiedaccess_instance.example
  id = "vai-1234567890abcdef0"
}
```

Using `terraform import`, import Verified Access Instances using the  `id`. For example:

```console
% terraform import aws_verifiedaccess_instance.example vai-1234567890abcdef0
```
