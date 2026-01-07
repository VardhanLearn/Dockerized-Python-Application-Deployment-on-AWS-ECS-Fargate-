**Dockerized Python Application Deployment on AWS ECS (Fargate)**

This project demonstrates how to **containerize a Python web application using Docker** and deploy it on **AWS ECS with Fargate**, using **Amazon ECR** for image storage and **Application Load Balancer (ALB)** for public access.

The setup follows **production-ready DevOps best practices** without managing EC2 instances.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
📌 **Project Overview**

• Containerized Python Flask application
• Docker image stored in Amazon ECR
• Serverless container deployment using ECS Fargate
• Application exposed via Application Load Balancer
• Centralized logging with CloudWatch
• Highly available & scalable architecture


<img width="617" height="431" alt="Screenshot from 2026-01-07 16-20-57" src="https://github.com/user-attachments/assets/5056b4a5-a676-4310-a01b-60f779f1c8d9" />

🛠 **Technologies Used**

• Docker • Python (Flask) • Gunicorn • AWS ECS (Fargate) • Amazon ECR
• Application Load Balancer • Amazon CloudWatch • AWS CLI
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
📂 **Project Structure**

<img width="609" height="196" alt="Screenshot from 2026-01-07 17-28-53" src="https://github.com/user-attachments/assets/607ad537-a6d8-4d3a-ab1f-d81dc70f8f35" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Deployment Steps**

1️⃣ **Configure AWS CLI**
    
    • aws configure

2️⃣ **Create ECR Repository**
    
    • aws ecr create-repository --repository-name ecs-fargate-python-app

3️⃣ **Authenticate Docker to ECR**
   
   • aws ecr get-login-password \
   | docker login \
   --username AWS \
   --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com

4️⃣ **Build Docker Image**
   
   • docker build -t ecs-fargate-python-app .

5️⃣ **Tag & Push Image**
  
   • docker tag ecs-fargate-python-app:latest <ECR_URI>:latest
   • docker push <ECR_URI>:latest

6️⃣ **Create ECS Cluster**
  
   • Launch Type: Fargate
   • Cluster Name: ecs-fargate-cluster

7️⃣ **Create Task Definition**
   
   • Launch type: Fargate
   • CPU: 0.5 vCPU
   • Memory: 1 GB
   • Container Port: 5000
   • Log driver: awslogs

8️⃣ **Create Application Load Balancer**

   • Type: Internet-facing
   • Listener: HTTP 80
   • Target Group: IP-based

9️⃣ **Create ECS Service**

   • Desired tasks: 2
   • Assign public IP: Enabled
   • Attach ALB to service

✅ **Verification**

   • Open the ALB DNS name in browser:
   • http://<alb-dns-name>


**Expected output:**

   • ECS Fargate App is running successfully!

📊 **Monitoring & Logs**

   • Container logs → Amazon CloudWatch
   • Metrics monitored:
   • CPU Utilization
   • Memory Usage
   • Task Health

🌟 **Advantages of ECS Fargate**

   • No EC2 management
   • Serverless container execution
   • Built-in high availability
   • Secure IAM-based access
   • Auto scaling support
   • Pay only for used resources

👤 **Author**

**Vardhan Kandregula DevOps Engineer** | AWS | Docker | Kubernetes | CI/CD

📌 This project is part of my DevOps learning and portfolio.

⭐ If you like this project

Give it a ⭐ on GitHub and feel free to fork or contribute!
