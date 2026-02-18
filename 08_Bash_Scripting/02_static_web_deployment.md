# 02 - Static Web Server Deployment Automation

This section documents the automation of deploying a static website using Bash.

Focus:
- Package installation
- Service lifecycle management
- Artifact download
- Deployment to web root
- Cleanup process

Tested on:
- CentOS (httpd)
- Ubuntu (apache2)

---

## 1. Basic Static Deployment Script

### Script: `deploy_static.sh`

```bash
#!/bin/bash

PACKAGE="httpd wget unzip"
SVC="httpd"
URL="https://www.tooplate.com/zip-templates/2098_health.zip"
ART_NAME="2098_health"
TEMPDIR="/tmp/webfiles"

echo "Installing Packages..."
sudo yum install $PACKAGE -y > /dev/null

echo "Starting and Enabling Service..."
sudo systemctl start $SVC
sudo systemctl enable $SVC

echo "Deploying Application..."
mkdir -p $TEMPDIR
cd $TEMPDIR || exit

wget $URL > /dev/null
unzip $ART_NAME.zip > /dev/null
sudo cp -r $ART_NAME/* /var/www/html/

echo "Restarting Service..."
sudo systemctl restart $SVC

echo "Cleaning Temporary Files..."
rm -rf $TEMPDIR

echo "Deployment Completed."
```

---

## 2. Teardown Script

### Script: `dismantle.sh`

```bash
#!/bin/bash

sudo systemctl stop httpd
sudo rm -rf /var/www/html/*
sudo yum remove httpd wget unzip -y
```

Purpose:
- Stop service
- Remove deployed files
- Remove installed packages
- Reset environment for clean rebuild

---

## 3. Workflow

1. Run `dismantle.sh` (optional clean state)
OA2. Run deployment script
3. Copy VM IP address
OA4. Access site in browser
5. Static site served from `/var/www/html`

---

OA## 4. Concepts Implemented

### Package Management
OA- `yum install`
- `apt install` (Ubuntu variant)

### Service Management
- `systemctl start`
OA- `systemctl enable`
- `systemctl restart`

### Artifact Deployment Pattern

```
Download → Extract → Copy → Restart
```

This mimics a simplified CI/CD deployment stage.

---

## 5. DevOps Relevance

This script demonstrates:

- Infrastructure bootstrapping
- Service provisioning
- Application deployment automation
- Repeatable environment rebuild
- Manual configuration management logic

Equivalent real-world patterns:

- EC2 user-data provisioning
- CI/CD deployment job
- Basic configuration management workflow

---

## 6. Limitations

- Not fully idempotent
- Always reinstalls packages
- Always restarts service
- No error handling
- No argument validation

These improvements were implemented in later sections.

---

## 7. Execution

```bash
chmod +x deploy_static.sh
./deploy_static.sh
```

After execution:
- Web server runs on port 80
- Static site available via VM IP address

