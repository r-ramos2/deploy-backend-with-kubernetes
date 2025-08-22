<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy Backend with Kubernetes

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks4)

**Author:** R  

---

## Deploy Backend with Kubernetes

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-eks4_6cfb382f2)

---

## Introducing Today's Project!

In this project, I will deploy the backend of an app on a Kubernetes cluster using Amazon EKS because it allows for scalable, managed container orchestration.

### Tools and concepts

I used Kubernetes, ECR, kubectl, and eksctl to deploy a containerized Flask backend on AWS EKS. Key concepts include using manifests (Deployment and Service) to define and manage application resources, storing Docker images in ECR, and using kubectl to interact with the Kubernetes cluster.

### Project reflection

This project took me approximately 2 hours. The most challenging part was correctly configuring and replacing the ECR image URI in the deployment manifest. My favorite part was applying the manifests and seeing the backend spin up across the cluster.

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The cluster's role in this deployment is to manage and run my app's backend containers using EKS, which handles scheduling, scaling, and networking automatically.

### Backend code

I retrieved backend code by cloning the GitHub repo using `git clone`. Pulling code is essential to this deployment because it provides the app files I need to containerize and deploy to the EKS cluster.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes needs a consistent, portable template to create and run containers across the cluster. Without an image, it would be difficult for Kubernetes to deploy the application reliably across different nodes or environments.

I also pushed the container image to a container registry, which is Amazon ECR. ECR facilitates scaling for my deployment because it allows Kubernetes to pull the latest version of my container image from a centralized, secure location whenever it spins up new pods, ensuring consistency and simplifying updates across the cluster.

---

## Manifest files

Kubernetes manifests are YAML configuration files that define the desired state of Kubernetes resources, such as Deployments and Services, to manage how applications run in a cluster. Manifests are helpful because they allow for consistent, automated, and repeatable deployment of applications by specifying all necessary parameters like container images, replicas, ports, and resource limits.

A Deployment manifest manages how Kubernetes runs and maintains multiple instances of an application, ensuring high availability, automatic scaling, and rolling updates. The container image URL in my Deployment manifest tells Kubernetes exactly which Docker image to pull from Amazon ECR so it can create and run the correct version of the backend application across the cluster.

A Service resource exposes a set of running containers (pods) in a Kubernetes cluster to internal or external traffic, ensuring reliable communication. My Service manifest sets up a NodePort service that routes incoming traffic on port 8080 to the backend pods labeled `nextwork-flask-backend`, making the application accessible from outside the cluster using the node’s IP and assigned port.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-eks4_b01876554)

---

## Backend Deployment!

To deploy my backend application, I installed the `kubectl` tool, gave it execution permission, and then ran `kubectl apply -f flask-deployment.yaml` and `kubectl apply -f flask-service.yaml` to create the Deployment and Service resources in my Kubernetes cluster based on my manifest files.

### kubectl

kubectl is the command-line tool for interacting with and managing Kubernetes resources inside a cluster. I need this tool to apply my manifest files and control how my application runs in the cluster. I can't use eksctl for the job because eksctl is designed for setting up and configuring the EKS cluster itself, not for managing the apps running inside it.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-compute-eks4_6cfb382f2)

---

## Verifying Deployment

---

---
