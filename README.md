![Alt text](/Host-a-Static-Website-on-AWS.png)
---
# Host a Static Website on AWS

## Project Overview

This project showcases the process of hosting a static HTML web application on AWS, leveraging various cloud services to ensure security, scalability, and high availability. By deploying the application on EC2 instances within a Virtual Private Cloud (VPC), we enhance network security while ensuring seamless access for users. The infrastructure is designed to be robust, utilizing an Auto Scaling Group and an Application Load Balancer to manage traffic and maintain optimal performance across multiple availability zones. 

The implementation follows best practices for networking and security, such as placing web servers in private subnets and utilizing a NAT Gateway for controlled outbound Internet access. Additionally, AWS Certificate Manager secures application communications, and Amazon Route 53 manages DNS records for efficient domain routing. With the help of GitHub for version control, updates to the website can be efficiently managed and deployed. This project provides a scalable, fault-tolerant, and automated approach to hosting static web content on AWS, making it an ideal solution for enterprises and developers seeking a cloud-based hosting solution.

## Architecture and Resources Used

The following AWS resources were configured for this project:

1. **Virtual Private Cloud (VPC)** – Configured with both public and private subnets across two different availability zones.
2. **Internet Gateway** – Facilitates connectivity between VPC instances and the Internet.
3. **Security Groups** – Acts as a firewall mechanism to regulate inbound and outbound traffic.
4. **Multiple Availability Zones** – Ensures reliability and fault tolerance.
5. **Public Subnets** – Used for NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint** – Securely connects to assets in both public and private subnets.
7. **Private Subnets** – Hosts the web servers (EC2 instances) for enhanced security.
8. **NAT Gateway** – Allows instances in private subnets to access the Internet.
9. **EC2 Instances** – Hosts the static website.
10. **Application Load Balancer (ALB)** – Distributes web traffic evenly to EC2 instances.
11. **Auto Scaling Group** – Automatically manages EC2 instances to ensure availability, scalability, and fault tolerance.
12. **GitHub** – Used for version control and collaboration.
13. **AWS Certificate Manager** – Secures application communications.
14. **Amazon SNS** – Sends notifications for Auto Scaling Group activities.
15. **Amazon Route 53** – Manages domain name registration and DNS configuration.

## Deployment Steps

### Prerequisites
- AWS account with necessary permissions.
- Domain name (optional but recommended).
- GitHub repository containing the web files.

### Installation Script

Below is the script used to set up and deploy the web application on an EC2 instance:

```bash
#!/bin/bash
# Switch to the root user
sudo su

# Update all installed packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project repository
git clone https://github.com/confyUK/Host-a-static-website-on-AWS.git

# Copy files to the Apache web root
cp -R Host-a-static-website-on-AWS/. /var/www/html/

# Clean up the cloned repository
rm -rf Host-a-static-website-on-AWS

# Enable Apache to start on boot
systemctl enable httpd

# Start Apache
systemctl start httpd
```

### Steps to Deploy
1. **Launch an EC2 Instance** – Choose Amazon Linux 2 as the AMI.
2. **Connect to the Instance** – Use SSH or EC2 Instance Connect.
3. **Run the Setup Script** – Copy and execute the above script.
4. **Configure Security Groups** – Allow HTTP (port 80) access.
5. **Set Up a Load Balancer** – To distribute traffic across instances.
6. **Register Domain (Optional)** – Configure Route 53 for a custom domain.

## Repository Structure

```
📁 Host-a-static-website-on-AWS
 ┣ 📂 web-files
 ┣ 📜 README.md
 ┣ 📜 install.sh
```

## Conclusion

By following this guide, you can successfully deploy a static website on AWS using EC2 instances. This setup ensures security, scalability, and high availability, making it suitable for production environments.

## Author
**confyUK**  
GitHub: [confyUK](https://github.com/confyUK)  

--
