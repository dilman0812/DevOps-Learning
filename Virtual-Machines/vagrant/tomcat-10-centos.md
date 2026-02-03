# Tomcat 10 Setup on CentOS Using systemctl

## Overview
This document describes the **manual installation and management of Apache Tomcat 10** on a **CentOS virtual machine** using **systemd (`systemctl`)**.

The objective of this exercise was to:
- Understand how Linux services are managed using systemd
- Run Tomcat as a dedicated non-root service
- Create and manage a custom systemd service unit

This setup was performed **manually** as part of learning Linux service management before automation.

---

## Tomcat Download
Tomcat 10 was downloaded directly from the Apache archive:

    wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.1.28/bin/apache-tomcat-10.1.28.tar.gz

---

## Extracting Tomcat
The downloaded archive was extracted:

    tar xzvf apache-tomcat-10.1.28.tar.gz

---

## Creating a Dedicated Tomcat User
A dedicated system user was created to run the Tomcat service:

    useradd --home-dir /opt/tomcat --shell /sbin/nologin tomcat

### Purpose
- Improves security by avoiding root execution
- Follows best practices for running services

---

## Tomcat Directory Setup
Tomcat files were copied to the service directory:

    cp -r apache-tomcat-10.1.28/* /opt/tomcat/

Ownership was assigned to the Tomcat user:

    chown -R tomcat.tomcat /opt/tomcat/

---

## Creating the systemd Service File
A custom systemd service file was created:

    vim /etc/systemd/system/tomcat.service

### Service File Content

    [Unit]
    Description=Tomcat
    After=network.target

    [Service]
    Type=forking
    User=tomcat
    Group=tomcat
    WorkingDirectory=/opt/tomcat

    Environment=JAVA_HOME=/usr/lib/jvm/jre
    Environment=CATALINA_HOME=/opt/tomcat
    Environment=CATALINA_BASE=/opt/tomcat

    ExecStart=/opt/tomcat/bin/startup.sh
    ExecStop=/opt/tomcat/bin/shutdown.sh

    [Install]
    WantedBy=multi-user.target

---

## Reloading systemd Configuration
After creating the service file, systemd was reloaded:

    systemctl daemon-reload

This allows systemd to recognize the new Tomcat service.

---

## Managing Tomcat Service
Tomcat was started and enabled using systemctl:

    systemctl start tomcat
    systemctl status tomcat
    systemctl enable tomcat

### Result
- Tomcat runs as a background service
- Service starts automatically on system boot
- Service status can be monitored via systemctl

---

## Key Concepts Learned
- systemd service lifecycle management
- Creating custom service unit files
- Running services as non-root users
- Using systemctl to start, stop, enable, and monitor services

---

## DevOps Learning Outcome
This exercise builds a strong foundation for:
- Linux service management
- Application server administration
- Automation using configuration management tools
- Running application servers in production environments

These same principles apply to:
- Cloud VMs
- CI/CD runners
- Container orchestration platforms

---
