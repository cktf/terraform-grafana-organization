# Terraform Grafana Organization

![pipeline](https://github.com/cktf/terraform-grafana-organization/actions/workflows/cicd.yml/badge.svg)
![release](https://img.shields.io/github/v/release/cktf/terraform-gitlab-organization?display_name=tag)
![license](https://img.shields.io/github/license/cktf/terraform-gitlab-organization)

**Organization** is a Terraform module useful for creating multiple teams, folders, dashboards, and datasources in **Grafana**

## Installation

Add the required configurations to your terraform config file and install module using command bellow:

```bash
terraform init
```

## Usage

```hcl
module "grafana" {
  source = "cktf/organization/grafana"

  name   = "MyOrg"
  admin  = "devops@myorg.web"
  admins = ["admin@localhost"]

  teams = {
    backend = {
      name  = "Backend"
      email = "backend@myorg.web"
    }
    frontend = {
      name  = "Frontend"
      email = "frontend@myorg.web"
    }
  }

  folders = {
    backend = {
      title = "Backend"
      permissions = {
        backend = "team:backend:Admin"
      }
    }
    frontend = {
      title = "Frontend"
      permissions = {
        frontend = "team:frontend:Admin"
      }
    }
  }
}

```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

This project is licensed under the [MIT](LICENSE.md).  
Copyright (c) KoLiBer (koliberr136a1@gmail.com)
