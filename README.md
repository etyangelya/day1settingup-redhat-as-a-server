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
