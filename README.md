# AWS DevSecOps Pipeline

This project demonstrates a complete **DevSecOps pipeline** using **Jenkins**, **Packer**, and **Terraform** on **AWS Cloud Infrastructure**. The solution is designed for a **single development environment** in a **single AWS region**, focusing on automation, infrastructure as code, and security integration throughout the CI/CD lifecycle.

The goal is to automate the process of:
- Building secure and reusable base images  [Link](https://github.com/AmanSingh881/Creating-Golden-Image-Using-Packer.git)
- Provisioning AWS infrastructure in a consistent and repeatable manner   [Link](https://github.com/AmanSingh881/Infrastructure-as-Code-Scalable-Web-Hosting-Architecture-with-AWS-and-Terraform.git)
- Running a secure CI/CD pipeline that builds, tests, and deploys application code [Link](https://github.com/AmanSingh881/aws-devsecops-pipeline/tree/main/CI%20CD%20Pipeline)
- Integrating security controls at each layer

---

## 📌 Key Features

### 🔧 Secure AMI Creation using Packer
- Automates the creation of hardened Amazon Machine Images (AMIs)
- Includes installation of required software, application dependencies, and system configurations
- Provides separate Packer templates for:
  - Application base images
  - Jenkins master node images

### ☁️ Infrastructure Provisioning using Terraform
- Uses **Terraform** to define and manage AWS infrastructure components in a consistent and automated manner.
- Adopts **modular design principles**, organizing infrastructure into reusable modules (e.g., networking, security, compute, DNS, certificates).
- Enables repeatable, scalable, and auditable infrastructure deployment.

#### Resources provisioned include:
- **Networking:**
  - Virtual Private Cloud (VPC) with public and private subnets
  - Route Tables and Internet Gateways
  - NAT Gateways for private subnet internet access

- **Identity and Access:**
  - IAM Roles, Instance Profiles, and Policies to follow least-privilege principle

- **Security:**
  - Security Groups and NACLs to control network traffic
  - Firewall rules scoped per environment (e.g., dev)

- **Compute:**
  - Amazon EC2 instances for Jenkins and application workloads
  - Auto Scaling Groups (ASG) for high availability and elasticity

- **Load Balancing:**
  - Application Load Balancer (ALB) to distribute traffic across ASG instances

- **DNS & Certificates:**
  - **Amazon Route 53** to manage DNS records and custom domain mapping for Jenkins and applications
  - **AWS Certificate Manager (ACM)** to provision and manage SSL/TLS certificates for securing HTTPS endpoints

- **Secrets Management:**
  - **AWS Secrets Manager** is used to securely store and retrieve sensitive data such as credentials, API tokens, and environment variables

### 🚀 CI/CD Pipeline using Jenkins
- Jenkins is installed and configured on a dedicated EC2 instance using a prebuilt AMI
- Pipeline automates:
  - Source code checkout
  - Terraform validation and deployment
  - Application build and deployment to EC2
- Integrates with **AWS Secrets Manager** to securely inject secrets (e.g., credentials, DB passwords, API keys) into build and deployment stages without hardcoding
- Uses scripted pipelines or Jenkins Job DSL for flexibility and version control

### 📦 Application Deployment on AWS
- Application is deployed using an Auto Scaling Group with EC2 instances based on the custom-built AMI
- Load balancer distributes traffic among healthy instances
- Application retrieves secrets dynamically at runtime from **AWS Secrets Manager**, ensuring sensitive configurations are never stored in code
- AMI updates and deployments are integrated into the CI/CD process

### 🔐 DevSecOps Tools Integration *(To be finalized)*
- Security scanning tools and practices will be integrated throughout the build and deploy process
- Final tools will be added and documented as the project progresses

---

Stay tuned as the project evolves with complete examples, configurations, and security best practices for modern cloud-native deployments.
