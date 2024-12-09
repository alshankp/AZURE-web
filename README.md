# AZURE-web
High Availability Website Deployment on Azure
In this project, I set up a highly available website on Microsoft Azure to make sure it stays online and runs smoothly even if there are issues in one of the regions. The goal was to ensure the website could handle traffic from users in different locations and stay available no matter what.

What I Did:

VM Setup in Two Regions: I deployed Azure Virtual Machines (VMs) in two different regions: Central US and West US. These VMs hosted different pages of the website:

Home Page: Hosted on VM2.
Upload Page: Hosted on VM1, where users can upload files to Azure Blob Storage.
Error Page: A custom error page (for 403 and 502 errors) was hosted in Azure Blob Storage.
Application Gateway Configuration: I used Azure Application Gateway to route users to the right page based on the URL:

When users visit example.com, they are sent to the home page on VM2.
When users go to example.com/upload, they are directed to the upload page on VM1.
If there's an error (like 403 or 502), the error page is shown from Azure Blob Storage.
Traffic Distribution with Traffic Manager: To make sure users are always directed to the right region, I set up Azure Traffic Manager. It automatically balances the traffic between the Central US and West US regions, ensuring the website is always available, even if one region has issues.

Secure Communication with VNet Peering: I used VNet-to-VNet Peering to securely connect the VMs and resources in both regions, so they could communicate with each other without any security risks.

Blob Storage for Error Pages and File Uploads: I used Azure Blob Storage to store the custom error page and a container called upload to store files that users upload.

Technologies Used:

Azure Virtual Machines (VMs): To host the website and its pages.
Azure Application Gateway: To route traffic to the right VM and show error pages.
Azure Traffic Manager: To balance traffic between regions for high availability.
Azure Blob Storage: For storing the error page and uploaded files.
Azure VNet Peering: To securely connect resources across regions.
This project helped me learn how to build a reliable, scalable website on Azure that can handle traffic from users in different regions and stay online, even during issues in one region.
