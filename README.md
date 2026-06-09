#Devops Intenship Assignment

##Objective

Deploy a java Spring Boot application on K8s & automate the deployment using Git Actions.
#Project Structure
devops-assignment/
├── src/main/java/com/example/demo/
│   ├── DemoApplication.java
│   └── HealthController.java
├── k8s/
│   ├── namespace.yaml
│   ├── secrete.yaml
│   ├── Deployment.yaml
│   └── Service.yaml
├── .github/workflows/
│   └── deploy.yml
├── Dockerfile
└── pom.xml
# Docker Image 
> Dockerfile created using eclipse-temurin:17-jdk-alpine
> Image built and pushed to DockerHub:
docker build -t bisheshbaidali/demo:latest  .
docker push bisheshbaidali/demo:latest

#K8s Deployment
>Minikube used for local Kubernetes cluster
>Applied all manifests:
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/secrete.yaml
kubectl apply -f k8s/Deployment.yaml
kubectl apply -f k8s/Service.yaml

# Deployment Steps
Kubernetes Resources Created:
Namespace: dev
Secret: app-secret (APP_NAME, APP_ENV)
Deployment: 2 replicas of the application
Service: ClusterIP on port 80

# Results 
Namespace dev: Active
Pods: 2/2 Running
Deployment: 2/2 Available
Service: ClusterIP created
Secret: app-secret created

# GitHub Actions CI/CD
Workflow triggers on every push to main branch:
Builds Java application with Maven
Builds Docker image
Pushes image to Docker Hub (bisheshbaidali/demo:latest)
Note: Kubernetes deployment done locally using Minikube.
 
 Note: Github action ma kubernetes deploy step hatako xu kina vanne
 github action cloud ma run hunxa 
  
 *** But maro minikube chai local machine ma run vako xa ***
