# Renuncientsub
# 🌐 Secure Static Website + Subdomain Hosting with CI/CD on AWS

This project showcases how to host a secure, high-performance static website and subdomain using **Amazon Web Services (AWS)**, integrated with **GitHub Actions** for continuous deployment.

## 📁 Live Domains
- 🌍 Main Domain: [https://renunciant.in](https://renunciant.in)
- 🧪 Subdomain: [https://devbytes.renunciant.in](https://devbytes.renunciant.in)

---

## 🚀 Project Overview

This system includes:
- 🔐 Private S3 Buckets (No public access)
- 🌐 CloudFront CDN (HTTPS + caching)
- 🔒 SSL via ACM (Amazon Certificate Manager)
- 🧱 OAC (Origin Access Control) for secure S3 delivery
- 🌍 Route 53 DNS with GoDaddy domain
- ⚙️ GitHub Actions to auto-deploy on `git push`

---

## 🔧 Architecture Diagram

```
+-------------+          +---------------+        +------------------+
|             |  Push    |               |  Sync  |                  |
|  Developer  +--------->| GitHub Actions+------->|    S3 Bucket     |
|             |          |               |        | (Private Access) |
+-------------+          +---------------+        +--------+---------+
                                                              |
                                                              | (via OAC)
                                                              v
                                                   +----------+-----------+
                                                   |      CloudFront      |
                                                   |   (with ACM HTTPS)   |
                                                   +----------+-----------+
                                                              |
                                                              v
                                                   +----------+----------+
                                                   |    End Users via    |
                                                   | https://yourdomain  |
                                                   +---------------------+
```

---

## 📦 File Structure

```
.
├── index.html
├── .github/
│   └── workflows/
│       └── deploy.yml
├── README.md
```

---

## ⚙️ GitHub Actions Workflow

Trigger: On push to `main` branch.  
Deploys static files to S3 and invalidates CloudFront cache.

Secrets Required:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION`
- `S3_BUCKET_NAME`
- `CLOUDFRONT_DISTRIBUTION_ID`

---
