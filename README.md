# High Availability Website Deployment on Azure
Overview
This project demonstrates the deployment of a high-availability website across multiple Azure regions, ensuring optimal traffic distribution, scalability, and fault tolerance using Azure Traffic Manager and Application Gateway.

Architecture
Azure Virtual Machines (VMs):

Deployed 4 VMs: 2 in Central US and 2 in West US.
VMs in each region are distributed across two subnets.
Storage Account:

Created a storage account with two containers:
static: Hosts the static website error page (error.html).
upload: Contains the upload page (upload.html) but without enabling static website hosting.
Application Gateway:

Configured separate application gateways for Central US and West US regions.
Central US:
Backend pool 1: Points to VM1 serving the upload page.
Backend pool 2: Points to VM2 serving the home page.
Routing rules include a custom error page and path-based routing for /upload.
Similar configuration for West US application gateway.
Traffic Manager:

Configured a Traffic Manager profile to distribute traffic between Central US and West US application gateways based on their public IPs.
Scripts and Code:

Cloned a Git repository to each VM containing vm1.sh and vm2.sh scripts for setup.
Configured config.py in VM1 of both regions to connect to the storage account's upload container.
Ran the application using sudo python3 app.py.
Key Technologies Used
Azure Traffic Manager: For load balancing between regions.
Azure Application Gateway: For routing traffic and implementing backend pools.
Python: For handling uploads and serving pages.
Git: For version control and deployment scripts.
Outcome
The website ensures high availability, with traffic managed efficiently between regions and seamless access to the upload and home pages. Custom error handling is also integrated for improved user experience.
