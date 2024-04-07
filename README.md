# UDR
Unified Data Repository (UDR)
# Unified Data Repository (UDR)
//===============================================================
The Unified Data Repository (UDR) is a critical component of the 5G Core Network (5GC) architecture. It serves as the centralized repository for storing and managing user-related data within a 5G network.

## UDR Functionality:
- **Data Storage:** UDR stores user subscription information, profiles, session states, and other user-related data.
- **Authentication and Authorization:** It facilitates authentication and authorization processes for user access to network services.
- **Accounting:** UDR plays a role in accounting functions, tracking usage and billing information for subscribers.

In simpler terms, the UDR ensures that user data is efficiently managed and accessible to various network functions, enabling seamless communication services in 5G networks.

//================================================================>

# Pipeline Overview
This Jenkins pipeline automates the build, testing, and deployment process for a Dockerized application using Jenkins, Docker, Helm, and AWS EKS.

## Pipeline Stages:
### Verify Branch:

Displays the current Git branch being built.

### Login to Dockerhub:
Logs in to Dockerhub using stored credentials.

### Pulling base image from Dockerhub:
Pulls the latest base image from Dockerhub (abodiaa/udr-base:latest).

Docker Build:
Lists Docker images. Builds a Docker image tagged as abodiaa/udr:latest. Lists Docker images again.

Scan Image for Common Vulnerabilities and Exposures:
Scans the Docker image for common vulnerabilities and exposures using Trivy. Generates a JSON report of vulnerabilities.

Pushing to Dockerhub:
Pushes the built Docker image (abodiaa/udr:latest) to Dockerhub.

Build and Package Helm Chart:
Packages the Helm chart located in ./helm/.

Configure Kubernetes Context:
Configures the Kubernetes context for AWS EKS cluster 5G-Core-Net.

Deploy Helm Chart on EKS:
Upgrades or installs the Helm chart named udr onto the EKS cluster.

Post-build Actions:
Always:
Archives the Trivy vulnerability report. Removes Docker images (abodiaa/udr:latest and abodiaa/udr-base:latest).
