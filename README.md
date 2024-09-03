# workpress-kubernetes



# WordPress Kubernetes Deployment

## Overview

The **WordPress Kubernetes Deployment** project demonstrates how to deploy a WordPress website on a Kubernetes cluster. This project provides a scalable and robust environment for hosting a WordPress website, utilizing Kubernetes' orchestration capabilities to manage and scale containers effectively. The deployment includes WordPress and a MySQL database, both running in separate containers within the Kubernetes cluster.

## Purpose

The main objective of this project is to showcase how to set up and deploy a WordPress site using Kubernetes. It provides an example of how to leverage Kubernetes' features like container orchestration, scalability, and automated deployment for hosting a popular content management system (CMS) like WordPress. This approach ensures a reliable and high-performance environment suitable for production-level web applications.

## Features

- **Kubernetes-Orchestrated Deployment**: Utilizes Kubernetes to deploy and manage WordPress and MySQL containers.
- **Scalable and Resilient**: Kubernetes provides automatic scaling and failover capabilities to ensure high availability.
- **Persistent Storage**: Ensures data persistence for WordPress and MySQL using Persistent Volume Claims (PVC).
- **Configurable and Secure**: Uses Kubernetes secrets and config maps for secure and dynamic configuration management.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Kubernetes Cluster**: A running Kubernetes cluster (e.g., Minikube, kind, GKE, EKS, or AKS).
- **kubectl**: Command-line tool to interact with the Kubernetes cluster. [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
- **Docker**: To build and manage container images. [Install Docker](https://www.docker.com/get-started).

### Installation

Follow these steps to set up and deploy WordPress on your Kubernetes cluster:

1. **Clone the repository:**

   ```bash
   git clone -b diffrent-device https://github.com/hasannader2040/wordpress-kubernetes.git
``

 2-  **Navigate to the project directory:**

```bash
cd wordpress-kubernetes
```

Create a Kubernetes Namespace (optional):

It is a good practice to create a separate namespace for the project:

```bash
kubectl create namespace wordpress
```

Apply Kubernetes Configurations:

Apply the Kubernetes deployment and service configuration files:

```bash
kubectl apply -f k8s/mysql-deployment.yaml
kubectl apply -f k8s/wordpress-deployment.yaml
```
This will deploy both MySQL and WordPress to your Kubernetes cluster.

Verifying the Deployment
To verify that the WordPress and MySQL pods are running, use the following command:

```bash
kubectl get pods -n wordpress
```
You should see output indicating that both the WordPress and MySQL pods are up and running.

Accessing the WordPress Site
To access the WordPress site, you need to expose it using a Kubernetes service. The default configuration uses a NodePort service:

Get the NodePort:

```bash
kubectl get svc -n wordpress
```
Find the NodePort for the WordPress service. It will be something like 30080:80/TCP.

Access WordPress:

Open your web browser and go to http://<Node_IP>:<NodePort>. Replace <Node_IP> with your Kubernetes cluster IP or localhost if using Minikube. Replace <NodePort> with the port number retrieved in the previous step.

## Usage
Here are some examples of how to manage the WordPress Kubernetes deployment:

Scaling the Deployment:

To scale the WordPress deployment to more replicas, use:

```bash
kubectl scale deployment wordpress --replicas=3 -n wordpress
```
This command will scale the WordPress pods to three replicas.

## Updating the Deployment:

To update the WordPress version or configuration, modify the wordpress-deployment.yaml file and apply the changes:

```bash
kubectl apply -f k8s/wordpress-deployment.yaml
```

## Deleting the Deployment:

To delete the entire deployment (both WordPress and MySQL), use:

```bash
kubectl delete -f k8s/mysql-deployment.yaml
kubectl delete -f k8s/wordpress-deployment.yaml
```

## Tools and Technologies
This project utilizes the following tools and technologies:

WordPress: A popular open-source content management system (CMS) used for building websites.
MySQL: A relational database management system used for storing WordPress data.
Kubernetes: An open-source platform designed to automate deploying, scaling, and operating application containers.
Docker: Used to containerize the WordPress and MySQL applications.
Contributing
Contributions are welcome! Please follow these steps to contribute:

1- Fork the repository.
2- Create a new branch (git checkout -b feature/your-feature-name).
3- Make your changes and commit them (git commit -m 'Add some feature').
4-Push to the branch (git push origin feature/your-feature-name).
5- Open a pull request.


## License
This project is licensed under the MIT License. See the LICENSE file for more details.


