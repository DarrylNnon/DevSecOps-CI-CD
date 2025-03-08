Production-Grade DevSecOps CI/CD Pipeline 🚀  

This project implements a secure, scalable, and automated CI/CD pipeline following DevSecOps best practices. The pipeline integrates security at every stage, ensuring high-quality, vulnerability-free applications deployed to production.  

## 📌 Key Features 
✅ Automated Security Scans: Integrated with SonarQube, Trivy, and Dependency-Check  
✅ Continuous Integration & Delivery: CI/CD pipeline built using Jenkins & GitLab  
✅ Infrastructure as Code (IaC): Automating setup using Docker & Shell scripts  
✅ Quality Gates: Enforcing high-code quality with SonarQube Webhooks  


## 🚀 Prerequisites 
Before setting up the pipeline, ensure you have:  

- Two AWS EC2 Instances:  
  - Build Server: `t2.micro` (15GB storage)  
  - SonarQube Server: `t2.medium` (4GB RAM)  


## ⚙️ Step 1: Install Required Jenkins Plugins  
Ensure the following plugins are installed on your Jenkins Master:  
- Parameterized Trigger Plugin  
- GitLab Plugin  
- Docker Pipeline  
- Pipeline: AWS Steps  
- SonarQube Scanner 
- Quality Gates  

## **🛠 Step 2: Install Dependencies on Build Server**  
Run the following command to install **Docker, Java8, Java11 & Trivy**:  
```sh
sudo ./setup.sh
```

## 🔍 Step 3: Deploy SonarQube on the t2.medium Server  
Execute the commands below to install and run SonarQube:  
```sh
sudo apt update 
sudo apt install -y docker.io 
sudo usermod -a -G docker ubuntu 
sudo docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
```

## 🔑 Step 4: Configure Jenkins Credentials  
Add the following credentials in Jenkins → Manage Credentials:  
- SonarQube Token: `Global Analysis Token` (Secret Text)  
- DockerHub Credentials: Username/Password  
- GitLab Credentials: Username/Password  
- Build Server Credentials: SSH Key for Jenkins Master  


## 🌍 Step 5: Enable SonarQube Webhook & Install Dependency-Check Plugin 
- Generate Webhook in SonarQube  
- Set Jenkins URL as:  
  ```sh
  http://<JENKINS_URL>:8080/sonarqube-webhook/
  ```


## 📢 Next Steps 
- Extend the pipeline to deploy secure cloud applications 
- Integrate RBAC, Secrets Management, and Compliance Checks  
- Implement Zero Trust Security for end-to-end protection  


## 📜 License 
This project is open-source and licensed under the MIT License.
