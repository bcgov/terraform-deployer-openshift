# terraform-openshift-deployer

![Lifecycle:Stable](https://img.shields.io/badge/Lifecycle-Stable-97ca00)

Terraform module which creates a service account to deploy applications on Openshift cluster.

## Usage

```hcl
terraform {
  required_version = ">= 0.15.3"
}

provider "kubernetes" {
  config_path = "~/.kube/config"
}

module "deployer" {
  source  = "bcgov/openshift/deployer"
  version = "0.10.0"

  name                  = "oc-deployer"
  namespace             = "xxxxxx-prod"
  privileged_namespaces = ["xxxxxx-dev", "xxxxxx-test", "xxxxxx-prod"]
}

output "sc_secret" {
  value = module.deployer.default_secret_name
}
```
