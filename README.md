# poc-tf-atl

![Terraform](https://img.shields.io/badge/Terraform-844FBA?logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Atlantis](https://img.shields.io/badge/Atlantis-Terraform%20workflow?logo=terraform&logoColor=white)

Terraform configuration for provisioning an Nginx web server through Docker, suitable for Atlantis-driven workflows.

## 🏗️ What it creates

- Downloads the `nginx:latest` Docker image.
- Creates a container named `Abes-Nginx-container` by default.
- Maps the container's port 80 to `localhost:8080`.

The container name can be changed with the `container_name` variable. The Docker provider is pinned to version `3.0.2` in `.terraform.lock.hcl`.

## 📋 Prerequisites

- [Terraform](https://developer.hashicorp.com/terraform/install)
- [Docker](https://docs.docker.com/get-docker/) with the daemon running

## 🚀 Usage

```sh
terraform init
terraform fmt -check
terraform validate
terraform plan
terraform apply
```

After applying, open <http://localhost:8080> or run:

```sh
curl http://localhost:8080
```

To use a custom container name:

```sh
terraform apply -var='container_name=my-nginx'
```

Remove the Docker image and container when finished:

```sh
terraform destroy
```

## 📤 Outputs

`terraform apply` reports the created Docker container ID and image ID. This repository has no application test suite or Atlantis configuration; Atlantis can run the standard Terraform plan/apply workflow against this root module.
