
🚀 MongoDB & Mongo Express Deployment on Kubernetes (AWS)


📌 Project Overview

This project demonstrates a production-like deployment of MongoDB on Kubernetes (kubeadm) running on AWS, with persistent storage using Amazon EBS CSI Driver and a Mongo Express web-based admin interface exposed via a LoadBalancer.

The goal of this project is to showcase real-world DevOps practices for running stateful applications on Kubernetes, integrating cloud-native storage, and managing secure access to databases.



🏗️ Architecture Overview

Kubernetes Cluster (kubeadm-based)

MongoDB deployed as a Kubernetes Deployment

Amazon EBS used for persistent storage (RWO)

AWS EBS CSI Driver for dynamic volume provisioning

Mongo Express as a web-based MongoDB admin UI

Kubernetes Secrets & ConfigMaps for secure configuration

LoadBalancer Service for external access


User
 │
 │  (HTTP :8081)
 ▼
Mongo Express (LoadBalancer Service)
 │
 │  (Internal Cluster Communication)
 ▼
MongoDB Service (ClusterIP)
 │
 │
 ▼
MongoDB Pod
 │
 ▼
Amazon EBS (Persistent Volume)



✨ Key Features

✔ Deploy MongoDB as a stateful workload on Kubernetes
✔ Use Amazon EBS (RWO) for persistent database storage
✔ Dynamic volume provisioning via AWS EBS CSI Driver
✔ Secure credentials management using Kubernetes Secrets
✔ Decoupled configuration using ConfigMaps
✔ Mongo Express UI for easy database administration
✔ External access via AWS LoadBalancer
✔ Designed to reflect real production environments



🧰 Technologies Used

Kubernetes (kubeadm)

Docker

MongoDB

Mongo Express

AWS EC2

Amazon EBS

AWS IAM

AWS EBS CSI Driver

YAML (Kubernetes Manifests)



🔐 AWS & Kubernetes Integration
AWS IAM Configuration

Created IAM User and Role

Attached policy:

AmazonEBSCSIDriverPolicy

Generated Access Keys

Stored credentials securely as Kubernetes Secrets

CSI Drivers Verification
kubectl get csidriver
kubectl get csinode


Both EBS and EFS CSI drivers are installed and recognized by the cluster.



📦 Kubernetes Resources
Secrets

MongoDB credentials stored securely using Kubernetes Secrets

Storage

Custom StorageClass using ebs.csi.aws.com

PersistentVolumeClaim with ReadWriteOnce access mode

Workloads

MongoDB Deployment with persistent storage

Mongo Express Deployment for database administration

Services

MongoDB exposed internally using ClusterIP

Mongo Express exposed externally using LoadBalancer



🌐 Accessing Mongo Express

Once the LoadBalancer service is created, retrieve the external IP:

kubectl get svc mongo-express-svc


Access Mongo Express from your browser:

http://<EXTERNAL-IP>:8081


Login using the MongoDB credentials stored in Kubernetes Secrets.



📸 Screenshots & Documentation

This repository includes:

Architecture diagrams

Kubernetes manifests

Step-by-step deployment process

AWS EBS volume verification



🎯 Real-World Value

This project reflects real enterprise scenarios where:

Databases must be persistent and reliable

Infrastructure is cloud-based

Storage is dynamically provisioned

Security best practices are enforced

Applications are containerized and scalable

It demonstrates the ability to operate stateful workloads on Kubernetes, a critical skill for DevOps and Cloud Engineers.



🧠 Skills Demonstrated

Kubernetes administration

Stateful application deployment

Cloud storage integration

AWS IAM & security

DevOps best practices

Production-ready system design




📎 Repository Structure
mongodb-project/
├── mongodb-secret.yaml
├── mongodb-sc.yaml
├── mongodb-pvc.yaml
├── mongodb-app.yaml
├── mongodb-svc.yaml
├── mongodb-cm.yaml
├── mongo-express-app.yaml
├── mongo-express-svc.yaml
└── README.md
├── screenshots/
├── Architecture



👨‍💻 Author

Mohannad Faisal
DevOps Engineer | Cloud & Kubernetes Enthusiast

🔗 GitHub: https://github.com/MOHANAD987



⭐ Final Note

If you find this project useful or inspiring, feel free to ⭐ star the repository or share feedback.
ترجمة
