# day1settingup-redhat-as-a-server
# Red Hat Server Setup Guide

This guide outlines the steps to configure a Red Hat-based system as a secure web server with SSH, HTTP/HTTPS (via Apache), and firewall services enabled.

## ✅ Requirements
- Red Hat Enterprise Linux (RHEL) 8/9 or compatible
- Root/sudo access
- Internet connectivity

---

## ⚙️ Step 1: Update System Packages

```bash
sudo dnf update -y


Step 2: Enable and Start SSH
SSH is usually pre-installed.

bash
Copy code
sudo systemctl enable sshd
sudo systemctl start sshd
Verify with: sudo systemctl status sshd

🌐 Step 3: Install Apache (HTTPD)
bash
Copy code
sudo dnf install httpd -y
Start and enable Apache:

bash
Copy code
sudo systemctl enable httpd
sudo systemctl start httpd
Test by visiting your server's IP in a browser: http://<your-server-ip>

🔥 Step 4: Configure the Firewall
Allow SSH, HTTP, and HTTPS services:

bash
Copy code
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload
Verify with: sudo firewall-cmd --list-all

🔒 Step 5: Install SSL/TLS (Optional)
To enable HTTPS with a self-signed certificate:

bash
Copy code
sudo dnf install mod_ssl -y
sudo openssl req -newkey rsa:2048 -nodes -keyout /etc/pki/tls/private/selfsigned.key \
  -x509 -days 365 -out /etc/pki/tls/certs/selfsigned.crt
Edit /etc/httpd/conf.d/ssl.conf to set your new key and cert paths, then restart Apache:

bash
Copy code
sudo systemctl restart httpd
You can later replace this with a Let's Encrypt cert using certbot.

✅ Done!
Your Red Hat server is now set up with:

SSH remote access

Apache serving HTTP and HTTPS

A configured and active firewall

🛠️ Optional: Check Statuses
bash
Copy code
sudo systemctl status sshd
sudo systemctl status httpd
sudo firewall-cmd --list-all


