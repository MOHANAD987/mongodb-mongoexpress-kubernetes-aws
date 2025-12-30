# 🚀 MongoDB & Mongo Express Deployment on Kubernetes (AWS)

![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)

## 📌 Project Overview
This project demonstrates a **production-ready deployment** of MongoDB on a Kubernetes cluster (kubeadm) running on AWS EC2. It showcases the integration of **Amazon EBS CSI Driver** for dynamic persistent storage and provides a web-based management interface via **Mongo Express**, securely exposed through an AWS LoadBalancer.

> **Objective:** To implement a secure, scalable, and persistent stateful workload on Kubernetes using cloud-native storage solutions.

---


## 🏗️ Architecture Overview
The system design ensures high availability and data durability by decoupling the database engine from the underlying storage.

### 🏛️ System Architecture Diagram
To better understand the infrastructure design, please refer to the high-resolution architecture blueprint located in the repository:

### 🖼️ **[architecture/](./architecture/)**



> **Infrastructure Blueprint:** This diagram illustrates the relationship between the Kubernetes workloads (Deployments & Services) and the AWS Cloud resources (EBS Volumes & IAM Policies), providing a comprehensive overview of the system's design.

### **🚦 Traffic & Data Flow:**
1. 🌐 **Public Access:** Users access **Mongo Express** via HTTP on port `8081` through an **AWS LoadBalancer**.
2. 🔄 **Internal Communication:** Mongo Express connects to the **MongoDB Service** (ClusterIP) within the cluster.
3. 💾 **Persistence:** The MongoDB Pod mounts a **Persistent Volume (PV)** backed by **Amazon EBS**, managed dynamically by the **CSI Driver**.

---


## ✨ Key Features
| Feature | Implementation Details |
| :--- | :--- |
| **Data Persistence** | **Amazon EBS (RWO)** ensures data survives Pod restarts or failures. |
| **Storage Management** | **Dynamic Provisioning** using a custom StorageClass (`ebs.csi.aws.com`). |
| **Security** | **K8s Secrets** for credentials and **ConfigMaps** for environment-specific settings. |
| **Administration** | **Mongo Express UI** for easy browser-based database management. |
| **Scalability** | Designed as a **Deployment** to leverage K8s orchestration and recovery. |

---


## 📸 Implementation Documentation (Step-by-Step)
This repository provides a comprehensive visual walkthrough of the entire deployment lifecycle. Detailed proof of implementation—from infrastructure provisioning to final application verification—is documented within the dedicated directory below:

### 📂 **[screenshots](./screenshots/)**

> This gallery serves as a step-by-step technical guide, showcasing the successful execution of all Kubernetes manifests and the seamless integration of AWS cloud-native resources.

---


## 🧰 Technologies & Tools
* **Orchestration:** Kubernetes (kubeadm)
* **Cloud Infrastructure:** AWS (EC2, IAM, EBS)
* **Database:** MongoDB
* **UI Management:** Mongo Express
* **Storage Integration:** AWS EBS CSI Driver
* **Automation:** YAML Manifests

---


## 🚀 How to Deploy

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/MOHANAD987/mongodb-project.git](https://github.com/MOHANAD987/mongodb-project.git)
    cd mongodb-project
    ```

2.  **Apply Storage & Security Manifests:**
    ```bash
    kubectl apply -f mongodb-sc.yaml
    kubectl apply -f mongodb-secret.yaml
    kubectl apply -f mongodb-cm.yaml
    kubectl apply -f mongodb-pvc.yaml
    ```

3.  **Deploy the Application:**
    ```bash
    kubectl apply -f mongodb-app.yaml
    kubectl apply -f mongo-express-app.yaml
    kubectl apply -f mongo-express-svc.yaml
    ```

4.  **Access the Dashboard:**
    * Retrieve the LoadBalancer URL: `kubectl get svc mongo-express-svc`
    * Open `http://<EXTERNAL-IP>:8081` in your browser.

---


## 📂 Repository Structure

```text

mongodb-project/
├── architecture/            # 📐 Reference Architecture Diagram
├── screenshots/             # 📸 Step-by-step Execution Screenshots
├── mongodb-secret.yaml      # 🔐 Encrypted Credentials
├── mongodb-sc.yaml          # 💾 StorageClass (ebs.csi.aws.com)
├── mongodb-pvc.yaml         # 📂 PersistentVolumeClaim
├── mongodb-app.yaml         # 🚀 MongoDB Deployment
├── mongodb-svc.yaml         # 🔌 Internal ClusterIP Service
├── mongodb-cm.yaml          # ⚙️ App Configurations
├── mongo-express-app.yaml   # 🖥️ Admin UI Deployment
├── mongo-express-svc.yaml   # 🌐 External LoadBalancer Service
├── LICENSE                  # ⚖️ MIT License
└── README.md                # 📖 Project Documentation



---





⚖️ License
This project is licensed under the MIT License. See the LICENSE file for details.

---




👨‍💻 Author
Mohanad Faisal
DevOps Engineer | Cloud & Kubernetes Enthusiast

---

