# terraform-aws-elasticache-scaling-helper

Terraform module which creates Redis ElastiCache Dynamic Scaling Helper resources on AWS.

## Description

Provision 

## Usage

### Complete

```hcl
module "elasticache_redis" {
  source                = "git::https://github.com/tmknom/terraform-aws-elasticache-redis.git?ref=tags/2.0.0"
  name                  = "example"
  number_cache_clusters = 2
  node_type             = "cache.m3.medium"

  engine_version             = "5.0.0"
  port                       = 56379
  maintenance_window         = "mon:10:40-mon:11:40"
  snapshot_window            = "09:10-10:10"
  snapshot_retention_limit   = 1
  automatic_failover_enabled = false
  at_rest_encryption_enabled = false
  transit_encryption_enabled = false
  apply_immediately          = true
  family                     = "redis5.0"
  description                = "This is example"

  subnet_ids         = var.subnet_ids
  vpc_id             = var.vpc_id
  source_cidr_blocks = var.source_cidr_blocks

  tags = {
    Environment = "prod"
  }
}
```

<!-- BEGINNING OF GENERATED BY TERRAFORM-DOCS -->

## Requirements

| Name      | Version |
| --------- | ------- |
| terraform | >= 0.12 |

## Providers

| Name | Version |
| ---- | ------- |
| aws  | n/a     |

## Inputs

## Outputs

| Name                                                   | Description                                                                |
| ------------------------------------------------------ | -------------------------------------------------------------------------- |
| elasticache_parameter_group_id                         | The ElastiCache parameter group name.                                      |
| elasticache_replication_group_id                       | The ID of the ElastiCache Replication Group.                               |
| elasticache_replication_group_member_clusters          | The identifiers of all the nodes that are part of this replication group.  |
| elasticache_replication_group_primary_endpoint_address | The address of the endpoint for the primary node in the replication group. |
| security_group_arn                                     | The ARN of the Redis ElastiCache security group.                           |
| security_group_description                             | The description of the Redis ElastiCache security group.                   |
| security_group_egress                                  | The egress rules of the Redis ElastiCache security group.                  |
| security_group_id                                      | The ID of the Redis ElastiCache security group.                            |
| security_group_ingress                                 | The ingress rules of the Redis ElastiCache security group.                 |
| security_group_name                                    | The name of the Redis ElastiCache security group.                          |
| security_group_owner_id                                | The owner ID of the Redis ElastiCache security group.                      |
| security_group_vpc_id                                  | The VPC ID of the Redis ElastiCache security group.                        |

<!-- END OF GENERATED BY TERRAFORM-DOCS -->

### Configure environment variables

```shell
export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
export AWS_DEFAULT_REGION=ap-southeast-1
```

### Installation

```shell
git clone git@github.com:tmknom/terraform-aws-elasticache-redis.git
cd terraform-aws-elasticache-redis
make install
```

### Makefile targets

```text
apply-complete                 Run terraform apply examples/complete
apply-minimal                  Run terraform apply examples/minimal
bump-version                   Bump version (Required argument 'VERSION')
check-format                   Check format code
clean                          Clean .terraform
destroy-complete               Run terraform destroy examples/complete
destroy-minimal                Run terraform destroy examples/minimal
diff                           Word diff
docs                           Generate docs
format                         Format code
help                           Show help
install                        Install requirements
lint                           Lint code
plan-complete                  Run terraform plan examples/complete
plan-minimal                   Run terraform plan examples/minimal
release                        Release GitHub and Terraform Module Registry
upgrade                        Upgrade makefile
```

### Releasing new versions

Bump VERSION file, and run `make release`.

### Terraform Module Registry

## License

Apache 2 Licensed. See LICENSE for full details.