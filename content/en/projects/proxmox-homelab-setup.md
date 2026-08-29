---
title: "Setting Up Proxmox: My Homelab Foundation"
date: 2026-06-20
draft: false
summary: "How I built a Proxmox VE host as the base of my homelab, and a full follow-along guide to set up your own."
tags: ["Proxmox", "Homelab", "Virtualisation"]
categories: ["Projects"]
showTableOfContents: false
---

## Summary

Proxmox VE is the foundation everything else in my homelab sits on. A free, Debian-based hypervisor. Lets me run multiple VMs and containers on a single box, with a proper web interface instead of SSH-only tinkering.

I run it on a repurposed mini PC. It now hosts my Docker containers, my Plex server, and a few test environments I use for practicing things I write about on the blog.

I picked it over alternatives like ESXi mainly because it's genuinely free, no feature-gated licensing, and it gave me hands-on exposure to virtualisation concepts that translate directly to enterprise environments.

## Stack

- Mini PC host (any reasonably modern x86 box with virtualisation extensions enabled in BIOS)
- Proxmox VE (latest stable release)
- A USB drive for the installer
- A second drive or partition for VM storage, separate from the boot drive if possible

## Follow-Along Guide

### 1. Prepare the installer

Download the Proxmox VE ISO from the official site and flash it to a USB drive using a tool like Balena Etcher or `dd` on Linux:

```bash
sudo dd if=proxmox-ve_8.x.iso of=/dev/sdX bs=4M status=progress conv=fsync
```

Double check `/dev/sdX` is actually your USB drive before running this. It's destructive.

### 2. Check BIOS settings before installing

Boot into BIOS and confirm virtualisation extensions (Intel VT-x or AMD-V) are enabled, along with VT-d or AMD-Vi if you plan to pass through hardware like a GPU or a USB device later. This is the step I missed first time round. Meant a full reinstall rather than a five second BIOS toggle.

### 3. Run the installer

Boot from the USB, select Proxmox VE, and step through the installer. Key choices:

- Target disk for the Proxmox install itself
- Country, timezone, keyboard layout
- A strong root password
- Network configuration, ideally a static IP so the management interface doesn't move around on you

### 4. First login and updates

Once installed, access the web UI at `https://<your-proxmox-ip>:8006` and log in as root. Before anything else, update the system:

```bash
apt update && apt full-upgrade -y
```

If you're not using a paid subscription, you'll also want to switch to the no-subscription repository so updates don't fail against the enterprise repo:

```bash
sed -i 's/^deb/#deb/' /etc/apt/sources.list.d/pve-enterprise.list
echo "deb http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve-no-subscription.list
apt update
```

### 5. Set up storage properly

Add your secondary drive as a storage target under Datacenter > Storage, separate from the boot drive. Keeping VM disks off the boot drive makes reinstalling Proxmox itself far less risky later.

### 6. Create your first VM or container

For lightweight services I lean toward LXC containers over full VMs where I can, since they share the host kernel and use noticeably less overhead. For anything needing a different OS or kernel-level isolation, a full VM makes more sense. Most of my Docker workloads fall into that camp.

### 7. Set up backups before anything else goes on top

The step I'd tell anyone not to skip. Configure scheduled backups under Datacenter > Backup before you build anything on top of the host. Learned this one the hard way after losing a VM to a bad update with no snapshot to fall back on. Wrote about that one on the blog.

## Lessons Learned

Check BIOS virtualisation settings before installing, not after.

Keep VM storage on a separate drive from the Proxmox boot install.

Set up scheduled backups immediately, not once something's already gone wrong.

LXC containers for lightweight services, full VMs for anything needing kernel isolation.

## What's Next

Working toward automating VM and container provisioning with Ansible rather than clicking through the web UI each time. Eventually want to run this site's build pipeline through an Ubuntu VM on this same host, via GitHub Actions.
