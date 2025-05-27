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
- Create  Helm default values for Redis.
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
   helm create microservice
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/01%20helm%20create%20micro.png" width=500 />
2. Delete all default templates and values created with the chart.
3. Create a new template for deployments under the templates directory.
4. Copy the base deployment configuration from the previous exercise.
5. Replace static values with placeholders using {{ .Values.variableName }} in camelCase format.
   
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/02%20deployment%20file%20template.png" width=500 />
    
6. Create a new template for services.
    
7. Copy the base service configuration from the previous exercise.

8. Replace static values with placeholders using {{ .Values.variableName }} in camelCase format.
    
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/03%20service%20file%20template.png" width=500 />
    
9. Create a values.yaml file that defines default values for all microservice variables.
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/04%20default%20values%20file.png" width=500 />
     
10. Create a custom value file for each microservice to override the default values.
    
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/05%20overwrites%20default%20values.png" width=500 />
     
11. Render the Kubernetes YAML manifests from the chart and values. It helps preview what will be applied to the cluster without  creating any resources. It’s useful for inspecting the output before deploying
    
    ```bash
    helm template -f email-services-values.yaml ./microservice    
    ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/06%20vaidate%20that%20the%20yaml%20files%20are%20correct.png" width=500 />
   
12. Validate the Helm chart structure and templates for common issues, required fields, and adherence to best practices. It helps catch errors before rendering or deployment.
    
    ```bash
    helm lint -f email-services-values.yaml ./microservice 
    ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/07%20using%20lint%20to%20check%20for%20issues.PNG" width=500 />
   
13. Ensure that there aren't pods running. 
    
    ```bash
    kubectl get pod
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/08%20checking%20current%20pods.PNG" width=500 />
   
14. Install a microservice via Helm CLI
    
    ```bash
    helm install -f email-services-values.yaml emailservice ./microservice 
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/09%20installing%20emailservice.PNG" width=500 />
   
15. Verify that the pods are running.
    
    ```bash
    kubectl get pod
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/10%20two%20pods%20email%20service%20deployed.PNG" width=500 />
   
16.  List the releases deployed by Helm in Kubernetes.
    ```bash
    helm ls
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/13%20pods.png" width=500 />
   


### Helm Chart for Redis
1. Create a Helm Chart for Redis.
    
   ```bash
   helm create redis
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/14%20creating%20new%20chart%20for%20redis%20and%20creating%20deployment%20and%20service%20file.png" width=500 />
   
2. Delete all default templates and values created with the chart.
3. Create a new deployment.yaml file
4. Copy the base deployment configuration from the previous exercise.
5. Replace values with placeholders using camelCase variables wrapped in {{}}
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/15%20parameterizing%20redis%20template%20with%20volumes.PNG" width=500 />
   
6. Create a new service.yaml file.
7. Copy the base service configuration from the previous exercise.
8. Replace values with placeholders using camelCase variables wrapped in {{}}

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/16%20redis%20service%20template.PNG" width=500 />
   
9. Create a values.yaml file that defines default values for all Redis variables.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/17%20redis%20default%20values.png" width=500 />
   
10. Create a custom value file for Redis to override the default values.

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/18%20overwriting%20redis%20default%20value.png" width=500 />
   
11. Render the Kubernetes YAML manifests from the chart and values. It helps preview what will be applied to the cluster without  creating any resources. It’s useful for inspecting the output before deploying

    ```bash
    helm template -f ./values/redis-values.yaml ./charts/redis
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/19%20testing%20redis%20chart%20is%20ok.png" width=500 />
   
12. Test the YAML files against the Kubernetes cluster using --dry-run to simulate the deployment without applying changes.

    ```bash
    helm install rediscart .charts/redis -f ./values/redis-values.yaml --dry-run
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/20%20testing%20files%20within%20the%20k8%20cluster.png" width=500 />
   

### Deploy Microservices Using a Script
1. Create a script that deploys all microservices in a single command.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/21%20executing%20script.PNG" width=500 />
  
2. Provide rights to execute the script
   ```bash
   chmod u+x install_script.sh
   ls - la
   /.install_script.sh
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/21%20executing%20script.PNG" width=500/>
   
3. Verify that all pods are running.

   ```bash
   kubectl get pods
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/22%20all%20pods%20running.PNG" width=500 />
   
4. Create a script that deletes all microservices in a single command.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/23%20uninstll%20script.png" width=500 />
   
5. Provide rights and execute the script

    ```bash
   chmod u+x uninstall.sh
   ls - la
   /.uninstall.sh
   ```
   

### Deploy Microservices Using Helmfile.
1. Install Helmfile using Homebrew.

   ```bash
   brew install helmfile
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/28%20install%20helm%20file%20available%20in%20brew.png" width=500 />
   
2. Create a Helmfile.yaml and define the release name, chart location, and associated values.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/26%2026%20helmfile%20structure%20releases.PNG" width=500 />
   
3. Specify configuration values directly in helmfile.yaml to override custom values files.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/27%20dfining%20the%20variables%20in%20the%20image%20section%20overwrites%20th%20values%20from%20the%20custom%20values%20file%20from%20the%20helmfile.png" width=500 />
   
4. Deploy microservices.
   
   ```bash
   helmfile sync
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/29%20helfile%20sync.png" width=500 />
   
5. List available charts

   ```bash
    helmfile list
    ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/30%20helmfile%20list.png" width=500/>

    
6. Access the Online Boutique using the public IP address of the LoadBalancer.

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes_Microservices_Helm/blob/main/Img/32%20microservices%20runing%20using%20a%20loadbalancer%20as%20single%20port.png" width=500 />
   
   
