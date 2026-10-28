# Landing zone baseline, local example only

Write Terraform for a small example. Do not run terraform, AWS CLI, or any network command. Do not apply or create cloud resources.

Resources:
- one VPC
- one public subnet and one private subnet
- one S3 bucket for logs, with all public access blocked

Files:
- main.tf
- README.md that says this is a local example and nothing was deployed

Use variables with safe defaults. No account IDs, no credentials, no real company or client names.
