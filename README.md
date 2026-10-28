# Landing Zone Example

This is a **local example only**. No cloud resources were deployed, no AWS account was
used, and no credentials are required. The Terraform files exist to demonstrate a
baseline landing zone pattern and can be read, validated, and discussed without
touching any infrastructure.

## What's in here

| File | Purpose |
|------|---------|
| `main.tf` | VPC, public subnet, private subnet, and an S3 log bucket |
| `SETUP.md` | Step-by-step notes on how this project was created |
| `SPEC.md` | The one-page spec that was given to Kiro |

## Resources defined (not deployed)

- **VPC** — `10.0.0.0/16`, DNS support and hostnames enabled
- **Public subnet** — `10.0.1.0/24`, routed through an internet gateway
- **Private subnet** — `10.0.2.0/24`, no outbound route (add a NAT gateway to enable one)
- **S3 log bucket** — all public access blocked, versioning enabled, AES-256 encryption at rest

## Validate locally without deploying

```bash
terraform fmt -check
terraform init -backend=false
terraform validate
```

`init -backend=false` downloads the AWS provider without configuring a backend. No
plan or apply was run.

## How this was made

The Terraform was written by [Kiro CLI](https://kiro.dev) from the single-page spec in
`SPEC.md`. See [SETUP.md](SETUP.md) for the exact commands used and the tool versions
involved.
