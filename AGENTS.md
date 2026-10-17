# Agent instructions

- This is a single-root Terraform project; the configuration is in `main.tf`, `variables.tf`, and `outputs.tf` (there are no packages or application source directories).
- The only provider is `kreuzwerker/docker` (`~> 3.0.2`), and the local `.terraform.lock.hcl` pins provider version `3.0.2`; run `terraform init` before validation in a fresh checkout.
- The configuration pulls `nginx:latest`, creates a container named by `var.container_name` (default `Abes-Nginx-container`), and maps container port 80 to host port 8080. Plan/apply therefore require a running Docker daemon and may change when `nginx:latest` changes.
- The focused verification sequence is `terraform fmt -check`, then `terraform validate`; use `terraform fmt` to fix formatting before re-running the check.
- Use `terraform plan` to preview and `terraform apply` to create/update the local Docker image and container; use `terraform destroy` to remove resources. Do not hand-edit `terraform.tfstate` or state backups.
- There is no test suite or CI configuration in this repository; Terraform formatting, validation, and (when Docker is available) plan are the relevant checks.
