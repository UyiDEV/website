# AltSchool Examination Documentation

This documentaion provides a guide to:
1. Setting up an Ubuntu EC2 instance for web hosting.
2. Installing and configuring Apache2 to serve your web content.
3. Securing your website with HTTPS using a free SSL certificate from Let’s Encrypt.
4. Deploying a custom domain with professional configurations.

Designed as more than just a tutorial, this project serves as a complete toolkit for creating a secure, scalable, and reliable web server aligned with modern web standards. Whether you're new to web hosting or an experienced developer, this repository will enhance your skills and deepen your understanding of hosting and web security.

## Prerequisites

Before diving into this project, here’s what you need to know to ensure a smooth experience:
1.  Basic Linux Command Skills: Familiarity with essential Linux commands will help you navigate and manage the server effectively.
2.  EC2 Instance Setup: You should understand how to launch an EC2 instance and configure security groups to allow HTTP and HTTPS traffic.
3.  Development Environment: Tools like Git Bash or Visual Studio Code (VSCode) will be your companions for managing files and running commands.
With these basics in place, you’re all set to get started!

## Step 1: Launching a Linux server (On AWS)

1. Go to the AWS Console, click “Launch Instance”, and name the instance “web-server”
2. Choose **Ubuntu** for the operating system.
3. Ensure the instance type is **free-tier eligible** to prevent extra charges.
4. Create a new key pair named **key-pair**.
5. Under the network settings, enable **HTTP** and **HTTPS** traffic from the internet.
6. Click **Launch Instance**, and your instance will be up and running.

## Part 2: Installing Apache2 Web Server

1. SSH into your instance using your preferred terminal, whether it’s **Gitbash**, **Visual Studio Code**, or **Termius**. Your instance should now be connected.
   
2. Run the following command to update your instance and install **Apache2**:

   ```bash
   sudo apt update -y
   sudo apt install apache2 -y
   ```

3. To check if Apache2 is running correctly, use the command below:

   ```bash
   sudo systemctl status apache2
   ```

## Part 3: Clone the Repository and Assign the Required Permissions

1. Clone the repository containing your HTML, CSS, and other files using `git clone`.
2. Verify the files with `ls` and navigate into the cloned repository.
3. Move the repository to `/var/www/` (e.g., **website**).
4. Duplicate the default Apache configuration file in the **sites-available** folder.
5. Edit the configuration file to include the necessary `ServerName`, `ServerAlias`, and `DocumentRoot`.
6. Apply the required permissions with `chown` and disable the default site using `a2dissite`.
7. Set a password for the instance with `sudo passwd ubuntu`.
8. Enable the new site configuration with `a2ensite`.
9. Reload, restart, start, and check Apache2 status using `systemctl`.

## Part 4: Verify IP and Configure HTTPS with a Free SSL Certificate

1. Verify the cloned webpage by copying the IP address of your instance and pasting it into a browser.
2. Create a domain for your webpage and connect it to your instance’s IP address (e.g., **exam.omoruyiosakue.tech**).

## Set up HTTPS using a free SSL certificate from Let’s Encrypt

1. Install the necessary packages:

   ```bash
   sudo apt update
   sudo apt install certbot python3-certbot-apache -y
   ```
   
2. Obtain the SSL certificate and configure HTTPS for your domain with:

   ```bash
   sudo certbot --apache -d exam.omoruyiosakue.tech
   ```

This command will automatically configure your Apache server to enable HTTPS.

## Verify the SSL Certificate

Once the SSL certificate is deployed, visit your domain (e.g., https://exam.omoruyiosakue.tech) and check for the secure connection indicated by the padlock icon in the address bar.

# Project Landing Page

**Website**: [omoruyiosakue.tech](https://exam.omoruyiosakue.tech)  
**IP Address**: [3.80.25.129](http://3.80.25.129/)  

Web-server without SSL ![Alt](/assets/screenshot.png "Website")
Web-server with DNS and SSL ![Alt](/assets/screenshot2.png "Website with SSL")
