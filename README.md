# Omoruyi Emmanuel Osakue Project Landing Page  

**Website**: []()
**IP Address**: []()

---

## **Project Overview**  

The **Osinachi Project Landing Page** is a demonstration of deploying a static web page on an Nginx web server hosted on an AWS EC2 instance. This project highlights the following key skills and configurations:  
- Setting up a Linux server environment.  
- Installing and configuring the Nginx web server.  
- Deploying a custom HTML page.  
- Securing the web server with SSL certificates using Certbot for HTTPS access.  

The deployed landing page introduces the project creator and provides relevant project details.  

---

## **Setup Instructions**  

Follow the steps below to replicate the setup of the **Osinachi Project Landing Page**.  

### **1. Provision an AWS EC2 Instance**  
- Log in to your AWS account and launch an EC2 instance.  
- Choose an Ubuntu 24.04 AMI for the server.  
- Select an appropriate instance type (e.g., `t2.micro`).  
- Configure the security group to allow the following traffic:  
  - HTTP (Port 80) for web traffic.  
  - HTTPS (Port 443) for secure web traffic.  
  - SSH (Port 22) for remote server access.  

### **2. Install the Nginx Web Server**  
Run the following commands on the server to install and start Nginx:  
```bash
sudo apt update
sudo apt install nginx -y
```  

### **3. Deploy the HTML Landing Page**  
1. Navigate to the default web root directory of Nginx:  
   ```bash
   cd /var/www/html
   ```  
2. Backup the default Nginx welcome page:  
   ```bash
   sudo mv index.nginx-debian.html index.html.bak
   ```  
3. Upload the custom `index.html` file to the directory.  
4. Restart Nginx to apply the changes:  
   ```bash
   sudo systemctl restart nginx
   ```  

### **4. Configure SSL with Certbot**  
1. Install Certbot and the Nginx plugin:  
   ```bash
   sudo apt install certbot python3-certbot-nginx -y
   ```  
2. Obtain and configure an SSL certificate for your domain:  
   ```bash
   sudo certbot --nginx -d osinachiproject.online
   ```  
3. Follow the prompts to:  
   - Enter your email address.  
   - Agree to the Terms of Service.  
   - Decline (optional) sharing your email address with the EFF.  

Certbot will automatically update Nginx configurations to redirect HTTP traffic to HTTPS.  

### **5. Verify Setup**  
- Open a browser and navigate to []() to confirm the secure connection.  
- Test SSL auto-renewal:  
   ```bash
   sudo certbot renew --dry-run
   ```  

---

## **Usage**  

To access the landing page, visit [https://osinachiproject.online](https://osinachiproject.online).  

---
