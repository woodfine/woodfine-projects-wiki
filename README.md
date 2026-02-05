# Woodfine Deployment: woodfine-projects-wiki

![Status](https://img.shields.io/badge/status-production-green.svg)
![Classification](https://img.shields.io/badge/class-CONFIDENTIAL-red.svg)
![Target](https://img.shields.io/badge/cloud-Google_Cloud_Platform-blue.svg)

**Infrastructure-as-Code (IaC) configuration for the Project-Specific Documentation deployment.**

## 🎯 Objective
This repository defines the infrastructure, content configuration, and "PointSav Protocol" pairing logic for the following sovereign asset:

* **Target VM:** `vm-woodfine-proj-wiki` (e.g., `vm-woodfine-landing`)
* **Base OS Image:** `mediakit-os` (Flavor: `app-knowledge`)
* **Public URL:** `https://wwww.projects.woodfinegroup.com`

## 🏛 Architecture (The Supply Chain)
This deployment sits at the end of the **Sovereign Supply Chain**:

1.  **Vendor (PointSav):** Builds the `mediakit-os` binary image.
2.  **Forge (GitHub):** Stores this config repo (`woodfine-[name]`).
3.  **Cloud (GCP):** Terraform pulls the binary + this config to create the live instance.

## 🛠 Deployment Commands
*Authorized Personnel Only.*

```bash
# 1. Authenticate with Woodfine GCP Credentials
gcloud auth login --update-adc

# 2. Initialize Terraform State
terraform init

# 3. Plan the Deployment (Dry Run)
terraform plan -var-file="production.tfvars"

# 4. Apply (Launch/Update VM)
terraform apply -var-file="production.tfvars"
