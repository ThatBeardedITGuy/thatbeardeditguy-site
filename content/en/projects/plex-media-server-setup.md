---
title: "Setting Up Plex on My Homelab"
date: 2026-07-03
draft: false
summary: "How I deployed Plex as a Docker container on my Proxmox homelab, with a full follow-along guide."
tags: ["Plex", "Docker", "Homelab"]
categories: ["Projects"]
showTableOfContents: false
---

## Summary

Plex was one of the first real services I deployed once Docker was running, and honestly the original reason I built the homelab in the first place.

It runs as a container alongside everything else, pulling media from a dedicated storage share. Genuinely useful way to get comfortable with hardware transcoding, volume mounts, and network configuration, all of which map onto broader self-hosting skills.

## Stack

- Docker container running the official Plex Media Server image
- A dedicated storage volume for media, kept separate from the container itself
- Network configured for local access, with remote access handled carefully rather than just opened wide

## Follow-Along Guide

### 1. Plan your storage layout before deploying anything

Decide where your media is actually going to live before you deploy the container. I keep media on a separate mounted volume from the Docker host's own disk, so the container itself stays disposable and the media survives even if I rebuild the container from scratch.

```bash
mkdir -p /mnt/media/{movies,tv,music}
```

### 2. Create the compose file

```yaml
services:
  plex:
    image: plexinc/pms-docker:latest
    restart: unless-stopped
    network_mode: host
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
    volumes:
      - ./config:/config
      - /mnt/media:/media
```

Using `network_mode: host` avoids some of the local network discovery headaches Plex can have behind Docker's default bridge networking, at the cost of a bit less network isolation. Worth the trade-off for a homelab.

### 3. Deploy the container

```bash
docker compose up -d
```

### 4. Complete setup through the web UI

Access Plex at `http://<vm-ip>:32400/web` and step through the setup wizard: sign in, name your server, and add your media libraries pointing at the mounted paths from inside the container, `/media/movies`, `/media/tv`, and so on.

### 5. Set up hardware transcoding if your hardware supports it

If your host has an iGPU capable of hardware transcoding, passing it through to the container significantly reduces CPU load when streaming to devices that need the stream transcoded rather than played back natively. Needs the device passed through at both the Proxmox VM config level and the Docker container level, so worth doing once storage and basic playback are already confirmed working.

### 6. Be deliberate about remote access

Plex offers built-in remote access, which is convenient but worth understanding before switching on. I run it through my reverse proxy with access restricted rather than exposing the Plex port directly to the internet. Partly for security, partly because it gave me a reason to actually learn reverse proxy configuration properly rather than skipping it.

## Lessons Learned

Keep media storage separate from the container so rebuilding the container doesn't touch the media itself.

`network_mode: host` solves more local discovery problems than it causes issues, for a homelab context specifically.

Hardware transcoding is worth the setup effort if your CPU would otherwise be doing the work.

Don't expose ports directly to the internet without thinking it through first. Route through something you control.

## What's Next

Want to add proper monitoring around transcoding load and storage usage. Likely feeding into the same dashboard I'm building out for the rest of the homelab, so there's one place to see the health of everything rather than checking each service individually.
