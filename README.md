# End-to-End automated APP deployment on GKE

This project provisions infrastructure on Google Cloud Platform (GCP) using Terraform, installs Jenkins on Google Kubernetes Engine (GKE), and sets up Single/Multi-branch Pipelines to build and deploy applications with DockerHub integration.

![project-image](https://github.com/abdelrahmanmetwally/End-to-End-CI-CD-Pipeline-on-GCP-with-Terraform-Provisioned-GKE-and-Jenkins/blob/main/project-image.png)
## Requirements
 **Ensure the following tools are installed**:
- Git
- Terraform
- Docker
- Google Cloud SDK

## how to use

1.clone this repo 
```
https://github.com/abdelrahmanmetwally/final-project-infrastructure.git
```
2. Navigate to Terraform directory.
3. Customize Values in "values.auto.tvars" as you want.
4. Create the backend bucket.
5. Initialize and apply the Terraform configuration:
```
terraform init
```
```
terraform apply
```

## Jenkins  configurations

Step 1: Access Jenkins service
```
kubectl get service -n jenkins
```


 Step 2: Get Jenkins admin password

```
kubectl exec -it <running-container-name> -n jenkins -- bash
   cat /var/jenkins_home/secrets/initialAdminPassword
```
Step 3: Configure the following inside Jenkins:
- GitHub Credentials
- DockerHub Credentials
- Kubeconfig Integration
- Jenkins Slave Node (using username/password auth)

Step 4: Create Jenkins pipelines
- Choose Single or Multibranch Pipeline
- Use branch: main
- Select “Build With Parameters”

Step 5: Create new node with credentials usernameandpassword.

- Note: If the node is offline, make sure you selected [Non-Verifying Verification Strategy - Launch agents via SSH ] while creating & connect the slave and Run.
```
service ssh start
chmod 777 /var/run/docker.sock
```

##  Access Your App
Get your app’s public IP
```
kubectl get service -n app
```
Open the EXTERNAL-IP with the correct port in your browser.

## Tear Down Infrastructure

```
terraform destroy
```
## Contributions
Contributions to enhance or expand this project are welcome! If you found any issue or have suggestions, please open an issue or submit a pull request.

