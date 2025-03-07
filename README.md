# Kubernetes Cluster with Kind

This repository contains a Kubernetes cluster configuration using [Kind](https://kind.sigs.k8s.io/). It includes various manifests for deploying a full-stack application consisting of:

## Part 1: Introduction

This project sets up a Kubernetes cluster using Kind. The cluster consists of multiple components, including a frontend, backend, database, and supporting services. The setup is designed for local development and testing of Kubernetes workloads, providing an easy-to-use environment to experiment with Kubernetes deployments.

## Part 2: Web Application

The web application consists of multiple components that work together to provide a full-featured service:

- **Frontend and Backend Manifests**: The frontend and backend are defined using Kubernetes manifests that deploy and manage these components efficiently.
- **Services**: The frontend and backend communicate through dedicated Kubernetes services, ensuring seamless interaction between components.
- **DaemonSet**: A DaemonSet is included to ensure that certain critical services run on all nodes in the cluster.
- **Dockerfile**: The application is containerized using a Dockerfile, allowing it to be built and deployed within the Kubernetes cluster.
- **LoadBalancer Service**: A LoadBalancer service is provided to expose the application externally, ensuring accessibility to users.
  ### Screenshots

    Here are some outputs from running the commands:
    ![Image](https://github.com/user-attachments/assets/e81ee0ef-8438-4800-8a68-90176da197f4)


    ![Image](https://github.com/user-attachments/assets/9aaf9514-2962-4900-b98a-9cfc82d6e9af)


    ![Image](https://github.com/user-attachments/assets/dc3c94c0-a7e1-4d91-b138-521deb4b5c46)


    ![Image](https://github.com/user-attachments/assets/76530fd8-9422-44c8-bc89-fdcc8c53a739)


    ![Image](https://github.com/user-attachments/assets/9f7b4e24-5ee5-4a06-8149-60f2ca96579f)


    ![Image](https://github.com/user-attachments/assets/d1b6e26f-e8d6-48ea-b572-666a6f30e1a2)


    ![Image](https://github.com/user-attachments/assets/53c9dcef-1d60-4c87-a341-0a2f7e270694)


  ![Image](https://github.com/user-attachments/assets/9ec169aa-87ba-4cd5-938b-07d84a1694c9)


  ![Image](https://github.com/user-attachments/assets/70191b53-ef31-484f-b4d7-dda5d49b118f)


  ![Image](https://github.com/user-attachments/assets/53d4e699-4160-434d-8df0-c9633c83ce7f)


## Part 3: Database and Management UI

This part of the setup includes the database layer and its associated management tools:

- **MongoDB Database**: A NoSQL database used for storing application data.
- **MongoDB Express UI**: A web-based management interface for interacting with the MongoDB database.
- **Frontend Accessibility**: The frontend is accessible via a browser using Nginx, providing a user-friendly interface.

### Screenshots

![WhatsApp Image 2025-03-06 at 04 56 27_7eabd2c8](https://github.com/user-attachments/assets/3c9fddcd-2221-45c6-a08b-00daa5b7deca)

![WhatsApp Image 2025-03-06 at 05 18 03_9350cf3c](https://github.com/user-attachments/assets/b9a845d6-cef4-4c6a-8cc3-c6f3a480574e)


## Questions

**Question 11**: The matchlabel of the replica itself doesn't match the label for the containers created, resulting in creation of the containers but they wont be managed by the replicaset since the labels dont match


**Question 12**: The command contains &&, but sh -c treats it as a single argument.
kind: deployment should be kind: Deployment (capital "D") since Kubernetes is case-sensitive.


**Question 13**: The command contains &&, but sh -c treats it as a single argument.


**Question 14**: kubectl get deployment <deployment-name> -o=jsonpath='{.spec.template.spec.containers[*].image}'


**Question 23**: The service remains in the Pending state when checking with kubectl get svc.
No external IP gets assigned (EXTERNAL-IP stays <pending>).
The service is not reachable outside the cluster.


**Question 24**: A DaemonSet ensures that a copy of a Pod runs on all (or specific) nodes in a Kubernetes cluster. Unlike Deployments or ReplicaSets, which manage a certain number of replicas distributed across nodes, a DaemonSet guarantees that each node gets exactly one instance of the Pod.


## Part2


1️⃣ Namespace

A Namespace is a way to logically isolate resources within a Kubernetes cluster. It helps organize different environments (e.g., dev, staging, production) or separate teams within the same cluster.

2️⃣ ConfigMap

A ConfigMap is a Kubernetes object used to store non-sensitive configuration data as key-value pairs. It helps decouple configuration from application code.

3️⃣ Secret

A Secret is similar to a ConfigMap but is used to store sensitive data like passwords, API keys, and TLS certificates.


4️⃣ Network Policy

A NetworkPolicy controls how pods communicate with each other and external networks. By default, Kubernetes allows all traffic between pods, but a NetworkPolicy can restrict this.


5️⃣ Taint and Toleration

Taints and tolerations control pod placement by preventing or allowing specific nodes to run certain workloads.

Use Cases:
Prevent non-critical workloads from running on critical nodes.
Assign workloads to specific hardware (e.g., GPU nodes).
Reserve dedicated nodes for specific applications.


6️⃣ Volume

A Volume is a way to provide persistent storage to Kubernetes pods. Unlike container storage, which is ephemeral, volumes persist even if a pod restarts.

Types of Volumes:
emptyDir → Temporary storage that lasts as long as the pod runs.
hostPath → Mounts a directory from the host machine.
PersistentVolume (PV) & PersistentVolumeClaim (PVC) → For persistent storage across pod restarts.
ConfigMap & Secret volumes → Store config files and credentials.
NFS, AWS EBS, Azure Disk, Google Persistent Disk → Cloud-based storage options.
