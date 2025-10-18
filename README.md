# Nginx Reverse Proxy Demo

## Overview
This demo shows how to run a Node.js app on a EC2 instance and expose it to the internet via a separate EC2 instance running Nginx as a reverse proxy.

## Architecture
- **Web Server (Backend):** Hosts a simple Node.js application on port `3000`.
- **Proxy Server (Frontend):** Runs Nginx configured as a reverse proxy on port `80`.
- **Traffic Flow:**  
  User → Proxy Server (Nginx) → Web Server (Node.js)

## How to run
1. Launch two EC2 instances in same VPC.
2. Configure security groups.
    - Backend Server: Allow HTTP (80) from Reverse Proxy
    - Reverse Proxy: Allow HTTP (80) from anywhere
4. Copy `node/` files to web-server, install Node and create systemd service.
5. Copy `nginx/reverse-proxy.conf` to proxy-server `/etc/nginx/sites-available/` and enable.
6. Test `http://<proxy-ip>/`.

## Files
- `node/server.js` — minimal Node server.
- `nginx/reverse-proxy.conf` — Nginx site config for proxying to web server.
