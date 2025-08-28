
# 🌐 AWS VPC with Linux – Secure Network Architecture

## 🚀 Project Overview  
This project demonstrates how to design a **secure and scalable AWS VPC** from scratch using Linux EC2 instances.  
We created a **VPC with Public & Private subnets**, custom route tables, and Internet Gateway integration.  
Finally, we used a **Bastion Host** to access private resources securely.  

---

## 🏗️ Architecture  

```
                         +-----------------------------+
                         |        AWS VPC              |
                         |     CIDR: 192.168.5.0/24     |
                         +---------------+-------------+
                                         |
         +-------------------------------+-------------------------------+
         |                                                               |
 +-------+--------+                                             +---------+-------+
 | Public Subnet  |                                             | Private Subnet   |
 | (Bastion Host) |                                             | (Private EC2)    |
 |  Public EC2    |                                             |  No Public IP    |
 +-------+--------+                                             +---------+-------+
         |                                                               |
         +-----------------+                       +---------------------+
                           |                       |
                    +------+-------+         +-----+--------+
                    | Internet GW  |         | Route Table  |
                    |   (IGW)      |         |  myroute     |
                    +--------------+         +--------------+
```

---

## 🛠️ Steps Followed  

### 1️⃣ Create VPC  
- **CIDR Block:** `192.168.5.0/24`  

### 2️⃣ Create Subnets  
- **Public Subnet** → For Bastion Host with auto-assign public IP enabled  
- **Private Subnet** → For internal instance only  

### 3️⃣ Internet Gateway Setup  
- Created & attached to the VPC  
- Routes public subnet traffic to the Internet  

### 4️⃣ Route Table Configuration  
- Created custom route table **myroute**  
- Associated public subnet with **IGW route**  

### 5️⃣ EC2 Instance Deployment  
- **Public EC2 (Bastion Host)** → SSH access with Public IP  
- **Private EC2** → Accessible only from Bastion Host  

### 6️⃣ Secure Access Flow  
- SSH into Public EC2  
- From Public EC2, SSH into Private EC2 using private IP  

---

## 🖥️ How to Connect  

1. **SSH into Bastion Host (Public EC2):**  
   ```bash
   ssh -i your-key.pem ec2-user@<Public-EC2-Public-IP>
   ```

2. **From Bastion Host, SSH into Private EC2:**  
   ```bash
   ssh ec2-user@<Private-EC2-Private-IP>
   ```

---

## 📋 Prerequisites  
- AWS Account  
- SSH Key Pair for EC2 Instances  
- Basic Linux command knowledge  

---

## 👩‍💻 Author  
**Prajakta Pandaram**  

---

## 📜 License  
This project is licensed under the **MIT License**.
