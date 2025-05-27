# ☸️ Kubernetes
## 📦 Demo 6 & 7: 
These exercises are part of **Module 10: Kubernetes with Helm** in the **TWN DevOps Bootcamp**. The goal is to create a reusable **Helm chart** for multiple microservices and deploy them efficiently using Helm best practices.

## 🚀 Technologies Used
- **Kubernetes (minikube)**: Container orchestration.
- **REDIS**: In-memory database.
- **DigitalOcean**: Cloud-managed K8s.
- **Linux**: Environment for CLI.
- **kubectl**: CLI to interact with Kubernetes.
- **Helm**: The package manager for Kubernetes that simplifies the deployment of complex applications using charts.
- **Helmfile**: A declarative tool to manage multiple Helm charts and releases.
  
## 📋 Prerequisites
- Ensure minikube is running.
- Ensure you have a Digital Ocean account.
- Kubectl is installed and configured to connect to your cluster.
- Docker is installed to build container images.
- Helm is installed

## 📦 Demo 6
## 📌 Objective
Build a flexible, reusable **Helm chart** to deploy existing microservices.

## 🎯 Features
- Define a Helm chart for Microservices.
- Define a common template for microservices.
- Define common default values for microservices.
- Define a custom values file for microservices.
- Define a Helm chart for Redis.
- Create  a Helm default values for Redis.
- Define a custom values file for Redis.
- Deploy microservices using a script.
- Deploy microservices using Helmfile.

## 📦 Demo 7
## 📌 Objective
Deploy microservices using Helmfile

## 🎯 Features
* Install Helmfile
* Define HelmFile
* Apply configuration.
* Uninstall microservices.
  

## 🏗 Project Architecture

<img src=""/>

## ⚙️ Project Configuration
### Helm Chart for Microservices
1. Create a Helm Chart for microservices.
   ```bash
   
   ```
   <img src="" width=500 />
3. Delete all default templates and values created with the chart.
4. Create a new deployment.yaml file under the templates directory.
5. Copy the base deployment configuration from the previous exercise.
    <img src="" width=500 />
6. Replace static values with placeholders using {{ .Values.variableName }} in camelCase format.
    <img src="" width=500 />
7. Create a new service.yaml file.
    <img src="" width=500 />
8. Copy the base service configuration from the previous exercise.
    <img src="" width=500 />
9. Replace static values with placeholders using {{ .Values.variableName }} in camelCase format.
    <img src="" width=500 />
10. Create a values.yaml file that defines default values for all microservice variables.
     <img src="" width=500 />
11. Create a custom value file for each microservice to override the default values.
     <img src="" width=500 />
12. Validate that all YAML files are correct.
    
    ```bash
    
    ```
   <img src="" width=500 />
   
13. Validate the YAML file for issues.
    
    ```bash
    
    ```
   <img src="" width=500 />
   
14. Ensure that the Kubernetes namespace is empty before installing.
    
    ```bash
    
    ```
   <img src="" width=500 />
   
15. Install a microservice via Helm CLI
    
    ```bash
    
    ```
   <img src="" width=500 />
   
16. Verify that the pods are running.
    
    ```bash
    
    ```
   <img src="" width=500 />
   
17. Confirm that Helm installed the chart successfully.

    ```bash
    
    ```
   <img src="" width=500 />
   


### Helm Chart for Redis
1. Create a Helm Chart for Redis.
    
   ```bash
   
   ```
   <img src="" width=500 />
   
3. Delete all default templates and values created with the chart.
4. Create a new deployment.yaml file
5. Copy the base deployment configuration from the previous exercise.
6. Replace values with placeholders using camelCase variables wrapped in {{}}
   
   <img src="" width=500 />
   
8. Create a new service.yaml file.
9. Copy the base service configuration from the previous exercise.
10. Replace values with placeholders using camelCase variables wrapped in {{}}
    
   <img src="" width=500 />
   
12. Create a values.yaml file that defines default values for all Redis variables.
    
   <img src="" width=500 />
   
14. Create a custom value file for Redis to override the default values.
    
   <img src="" width=500 />
   
16. Validate that the YAML files are syntactically correct.

    ```bash
    
    ```
   <img src="" width=500 />
   
18. Test the YAML files against the Kubernetes cluster using --dry-run to simulate the deployment without applying changes.

    ```bash
    
    ```
   <img src="" width=500 />
   

### Deploy Microservices Using a Script
1. Create a script that deploys all microservices in a single command.
2. Create a script that deletes all microservices in a single command.

### Deploy Microservices Using Helmfile.
1. Install Helmfile using Homebrew.

   ```bash
   ```
   <img src="" width=500 />
   
3. Create a Helmfile.yaml and define the release name, chart location, and associated values.

   <img src="" width=500 />
   
5. Specify configuration values directly in helmfile.yaml to overrides custom values files.

   <img src="" width=500 />
   
7. Deploy microservices.
   
   ```bash
   
   ```
   <img src="" width=500 />
   
9. Access the Online Boutique using the public IP address of the LoadBalancer.

   <img src="" width=500 />
   
   
