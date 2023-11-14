# Simple CI/CD image with Terraform and AWS CLI

This repository contains a simple Docker image with Terraform and AWS CLI installed. The image is based on the
Python 3.12 image and contains the following tools:

- Terraform
- AWS CLI
- SOPS
- jq

The image is intended to be used as a base image for CI/CD pipelines.

## Usage

The image is available on GitHub package repository as `ordergroup/terraform-ci-image:latest`. The image can be used as
a base image for
CI/CD pipelines. For example, in Gitlab CI, the following configuration can be used:

```yaml
image: ordergroup/terraform-ci-image:latest

stages:
  - validate
  - plan
  - apply

validate:
  stage: validate
  script:
    - terraform init
    - terraform validate

plan:
  stage: plan
  script:
    - terraform init
    - terraform plan

apply:
  stage: apply
  script:
    - terraform init
    - terraform apply
```


