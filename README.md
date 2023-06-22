# CI/CD-project-ITI

### This repository contains Terraform configuration for setting up infrastructure on Google Cloud Platform (GCP) using terraform as (IAC), Installing Jenkins and build Single/Multi-branch pipeline to build and deploy an application on GKE

## Requirements

git
Terraform
Docker
Google Cloud SDK
A bucket as a backend to  terraform.

## how to use

1.clone this repo 
```
https://github.com/abdelrahmanmetwally/final-project-infrastructure.git
```
2.Change Directory to terraform-files
3.Customize Values in "values.auto.tvars" as you want.
4. create the backend bucket 
5.Run terraform commands:
```
terraform init
```
```
terraform apply
```
