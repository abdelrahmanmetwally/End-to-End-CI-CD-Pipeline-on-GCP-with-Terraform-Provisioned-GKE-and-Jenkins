# CI/CD-project-ITI

This repository contains Terraform configuration for setting up infrastructure on Google Cloud Platform (GCP) using terraform as (IAC), Installing Jenkins and build Single/Multi-branch pipeline to build and deploy an application on GKE

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

## for jenkins slave configurations


1.open Jenkins & create users and passwords.
```
   kubectl get service -n jenkins 
```
2.Exec your running container and get first password

```
kubectl exec -it <running-container-name> -n jenkins -- bash
   cat /var/jenkins_home/secrets/initialAdminPassword
```
3.Configure github,dockerHub,kubeconfig and slave (node: "jenkins,123456") credentials.

4.Create Single/Multibransh Pipline from Git repo

5.Create new node with credentials usernameandpassword.

note: If node is offline make sure you selected [Non Verifiying Verification Stratgey - Launch agents via SSH ] while creating & connect slave and Run.
```
service ssh start
chmod 777 /var/run/docker.sock
```
6.Choose a branch and click build now.

7.In case you run single pipline: after choosing Git credentails type
branch: main
JenkinsFile
build: select Build With Parameters

8.To get app url Run:

```
kubectl get service -n app
```
"Copy External-ip with specific port and access it from browser"
### finally 
To Destroy All Resources Run [Type 'yes' to confirm]
```
terraform destroy
```
