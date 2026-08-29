---
title: "Running My Homelab Services in Docker"
date: 2026-06-27
draft: false
summary: "How I moved my homelab services into Docker containers on top of Proxmox, with a follow-along guide to set it up yourself."
tags: ["Docker", "Homelab", "Self-Hosting"]
categories: ["Projects"]
showTableOfContents: false
---

## Summary

Once Proxmox was running, the next decision was how to actually deploy the services I wanted to self-host. Plex, a reverse proxy, a handful of small utilities.

Rather than a full VM for each one, I run a single lightweight Ubuntu VM and deploy everything inside it as Docker containers, managed through Compose. Each service is isolated. Easy to update independently. Easy to tear down and rebuild without touching anything else running alongside it.

Turned out to be a genuinely good way to practice change management thinking on a small scale too. Every container is its own blast radius. If an update to one breaks something, it doesn't take the others with it. Rolling back is usually just pulling the previous image tag.

## Stack

- Ubuntu Server VM running on Proxmox
- Docker Engine and Docker Compose
- Portainer for a web UI to manage containers without living in the CLI full time
- A reverse proxy container (I use Caddy) to handle routing and HTTPS certificates for services

## Follow-Along Guide

### 1. Provision the VM

Create a new Ubuntu Server VM in Proxmox with a reasonable baseline: 2 vCPUs, 4GB RAM, and 32GB disk is enough to start, scaling up if you add more services later. Install Ubuntu Server as normal and apply updates.

### 2. Install Docker

```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Add your user to the docker group so you're not prefixing every command with `sudo`:

```bash
sudo usermod -aG docker $USER
```

Log out and back in for that to take effect.

### 3. Set up a project structure

I keep each service in its own directory with its own `docker-compose.yml`, rather than one giant compose file for everything. Keeps updates and rollbacks scoped to a single service.

```bash
mkdir -p ~/docker/portainer
cd ~/docker/portainer
```

### 4. Deploy Portainer first

Portainer gives you a web UI over Docker itself, which makes managing the rest of the stack much easier than pure CLI, especially early on.

```yaml
services:
  portainer:
    image: portainer/portainer-ce:latest
    restart: unless-stopped
    ports:
      - "9443:9443"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data
volumes:
  portainer_data:
```

```bash
docker compose up -d
```

Access it at `https://<vm-ip>:9443` to finish setup.

### 5. Add a reverse proxy

For anything you want accessible with a proper domain and HTTPS rather than an IP and a port number, a reverse proxy is worth setting up early rather than bolting it on later once you've got a dozen services to retrofit.

### 6. Deploy services one at a time

Add new services the same way. Their own directory, their own compose file, tested individually before moving on. That's where the isolation really pays off. If a new service's compose file has an issue, it doesn't affect anything already running.

## Lessons Learned

One compose file per service rather than one giant stack file. Keeps updates and rollbacks scoped properly.

Set up Portainer early. Makes the rest of the process considerably less painful.

Named volumes over bind mounts where possible. Migrating a named volume to new hardware later is simpler.

Test each new service in isolation before assuming it'll play nicely alongside everything else.

## What's Next

Want to move from manually running `docker compose up` per service toward proper GitOps. Compose files in a Git repo, deployed automatically, tying into the same GitHub Actions pipeline I'm planning for this site.
