# HIGHLY-AVAILABLE-WEB-APPLICATION-.
# 🚀 Highly Available Web Application using Auto Scaling & Load Balancer

## 📌 Project Overview
This project demonstrates how to build a highly available and scalable web application on AWS.  
It solves the problem of application crashes during high traffic by automatically adjusting resources.

---

## 🎯 Objective
- Build a highly available architecture  
- Automatically scale EC2 instances based on demand  
- Avoid single point of failure  

---

## 🛠️ AWS Services Used
- EC2 (Elastic Compute Cloud)
- Auto Scaling Group (ASG)
- Application Load Balancer (ALB)
- Amazon VPC
- CloudWatch

---

## 🏗️ Architecture

### 🔹 Networking Setup
- Created Custom VPC
- Created 2 Public Subnets (Different AZs)
- Attached Internet Gateway
- Configured Route Tables

---

### 🔹 Launch Template
- Amazon Linux AMI used
- Instance type: t2.micro
- User Data Script:

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Version 1 - Highly Available App</h1>" > /var/www/html/index.html
```

---

### 🔹 Auto Scaling Group
- Minimum: 2 instances
- Maximum: 5 instances
- Desired: 2 instances
- Multi-AZ deployment enabled
- Scaling Policy:
  - Scale Out: CPU > 70%
  - Scale In: CPU < 30%

---

### 🔹 Application Load Balancer
- Listener: HTTP (Port 80)
- Target Group attached with ASG
- Health Check Path: `/`

---

## 🔁 High Availability Strategy
- Application deployed in multiple Availability Zones  
- Load Balancer distributes traffic  
- Auto Scaling replaces failed instances automatically  

---

## 🧪 Testing

### ✅ Failover Test
- Terminated one EC2 instance manually  
- ASG launched new instance automatically  
- Application remained available  

---

### ✅ Load Testing
- Generated traffic manually  
- Observed automatic scaling of instances  

---

### 📊 Monitoring
- Used CloudWatch for:
  - CPU Utilization
  - Scaling events

---

## 📸 Screenshots
(Add your screenshots here)
- VPC Setup
- Subnets
- Load Balancer
- Auto Scaling Group
- CloudWatch Metrics

---

## 📂 Project Structure
```
.
├── README.md
├── screenshots/
│   ├── vpc.png
│   ├── alb.png
│   ├── asg.png
│   ├── scaling.png
```

---

## 💡 Key Learnings
- High Availability architecture
- Auto Scaling implementation
- Load balancing concept
- AWS monitoring using CloudWatch

---

## 🔚 Conclusion
This project demonstrates a scalable, fault-tolerant system that can handle traffic spikes and maintain application availability.

---

## 🙌 Author
**Om Hivarkar**  
AWS DevOps Fresher

