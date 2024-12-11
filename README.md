# High Availability Website Deployment on Azure 🚀

This project demonstrates how to set up a **highly available website** on **Microsoft Azure** using **Virtual Machines (VMs)**, **Application Gateway**, and **Traffic Manager**. The setup ensures that your website remains accessible even if one Azure region goes down. Perfect for beginners exploring Azure's cloud capabilities!

---

## **Features**

- High availability using Azure Traffic Manager across regions.
- Efficient load balancing within regions using Application Gateway.
- Custom welcome page with Apache installed on VMs.
- Beginner-friendly step-by-step guide for easy setup.

---

## **Table of Contents**

- [Overview](#overview)
- [Project Architecture](#project-architecture)
- [Prerequisites](#prerequisites)
- [Step-by-Step Instructions](#step-by-step-instructions)
  - [1. Create Virtual Machines](#1-create-virtual-machines)
  - [2. Configure Application Gateway](#2-configure-application-gateway)
  - [3. Set Up Traffic Manager](#3-set-up-traffic-manager)
- [Testing the Setup](#testing-the-setup)
- [Enhancements](#enhancements)
- [License](#license)

---

## **Overview**

In this project, we deploy a web application in two Azure regions (**Central US** and **West US**) and distribute traffic using:

1. **Azure Traffic Manager** for region-based load balancing.
2. **Azure Application Gateway** for load balancing within each region.

---

## **Project Architecture**

```plaintext
Internet
   |
Azure Traffic Manager
   |
-----------------------------------
|                                 |
Region 1                         Region 2
Application Gateway             Application Gateway
|                               |
VMs                             VMs
```

---

## **Prerequisites**

- **Azure Account:** Create one at [Azure Free Trial](https://azure.microsoft.com/free/).
- **Basic Knowledge:** Familiarity with Azure services like VMs and Traffic Manager.
- **Tools:** Azure Portal (preferred), Azure CLI (optional).

---

## **Step-by-Step Instructions**

### **1. Create Virtual Machines**

1. **Deploy VMs in Two Regions:**
   - Deploy **2 VMs** in **Central US** and **2 VMs** in **West US**.
   - Use **Ubuntu 22.04** for the OS.

2. **Install Apache Web Server:**
   SSH into each VM and run:
   ```bash
   sudo apt update
   sudo apt install apache2 -y
   echo "<h1>Welcome to Region X</h1>" | sudo tee /var/www/html/index.html
   ```
   Replace `Region X` with the VM's region (e.g., `Central US` or `West US`).

---

### **2. Configure Application Gateway**

1. **Create Application Gateway:**
   - In the **Azure portal**, create an Application Gateway for each region.
   - Add the VMs in that region as backend targets.
   - Create routing rules to distribute traffic within the region.

---

### **3. Set Up Traffic Manager**

1. **Create Traffic Manager Profile:**
   - Go to **Traffic Manager Profiles** in the Azure portal.
   - Select **Performance Routing**.
   - Add endpoints:
     - **Central US Application Gateway**
     - **West US Application Gateway**

---

## **Testing the Setup**

1. Access your Traffic Manager's **DNS Name** in the browser.  
2. Test fault tolerance by stopping VMs in one region to confirm traffic is routed to the other region.

---

## **Enhancements**

1. **SSL/TLS Integration:** Secure your website using Azure Application Gateway’s SSL capabilities.  
2. **Autoscaling:** Enable autoscaling for VMs to handle traffic spikes.  
3. **Monitoring:** Use Azure Monitor for alerts and performance metrics.  

---

## **License**

This project is licensed under the MIT License. Feel free to use and modify it for your own projects!

---

## **Feedback**

We love contributions and feedback! Feel free to open an issue or submit a pull request. If this project helped you, give it a ⭐️ and share it with others!
