# CredPal DevOps Assessment: Production-Ready Node.js Stack
This repository contains a fully automated, secure, and scalable infrastructure and CI/CD pipeline for a Node.js application integrated with Docker Hardened PostgreSQL database Image.

## Project Structure
├── .github/workflows/  # CI/CD Pipeline Definitions
├── app/production/     # Node.js Application Source
├── IaC/*               # Terraform IaC for Azure Resources
├── assets/             # Evidence, Screenshots & Diagrams

## CI/CD & Reliability
* Blue-Green Deployment: Utilized Azure Deployment Slots. New code is deployed to the staging slot and "warmed up" * before being swapped to production for Zero Downtime.
* Automated Rollback: If health checks fail in the staging slot, the swap is aborted.
* Pipeline Persistence: Used GitHub Actions caching for npm to optimize build times.

<p align="center">
  <img src="https://raw.githubusercontent.com/ugwulo/credpal/main/assets/deployment-env-rollback.png" alt="Rollback environment"/>
</p>


Terraform version Used: Terraform v1.14.0
Azure Provider version = "4.42.0"


## Test the endpoint /process
curl -X POST https://URL/process \
  -H "Content-Type: application/json" \
  -d '{"userId": "123", "amount": 5000, "currency": "NGN"}'