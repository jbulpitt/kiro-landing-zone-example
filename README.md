# Landing Zone Baseline — Local Example Only

> **Nothing in this repository has been deployed. No AWS resources were created.**
> This is a local Terraform code example for reference and learning purposes only.

## What is this?

A minimal Terraform configuration that models a basic AWS landing zone baseline. It is
intended as a starting point or teaching aid — not a production deployment.

## Resources defined in main.tf

| Resource | Description |
|---|---|
| `aws_vpc.main` | A VPC with DNS support enabled |
| `aws_subnet.public` | A public subnet (instances receive a public IP) |
| `aws_subnet.private` | A private subnet (no public IP assignment) |
| `aws_internet_gateway.main` | Internet gateway attached to the VPC |
| `aws_route_table.public` | Route table directing `0.0.0.0/0` through the internet gateway |
| `aws_s3_bucket.logs` | S3 bucket for logs — public access fully blocked, versioning and SSE-S3 encryption enabled |

## Variables

All variables have safe defaults. No credentials, account IDs, or real company names are
used anywhere in this codebase.

| Variable | Default | Description |
|---|---|---|
| `aws_region` | `us-east-1` | AWS region |
| `vpc_cidr` | `10.0.0.0/16` | VPC CIDR block |
| `public_subnet_cidr` | `10.0.1.0/24` | Public subnet CIDR |
| `private_subnet_cidr` | `10.0.2.0/24` | Private subnet CIDR |
| `availability_zone` | `us-east-1a` | AZ for both subnets |
| `project` | `landing-zone` | Name prefix applied to all resources |

## Requirements

- Terraform >= 1.5.0
- AWS provider ~> 5.0

## Usage (if you choose to deploy)

If you decide to deploy this to a real AWS account, you are responsible for reviewing the
configuration, understanding the costs, and supplying valid credentials. This project does
**not** configure a remote backend — add one before sharing state with a team.

```bash
terraform init
terraform plan
terraform apply
```

To destroy all resources afterwards:

```bash
terraform destroy
```

## License

This example is provided as-is with no warranty. Use at your own risk.
