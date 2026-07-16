# Ubuntu Server Setup

## Overview

This runbook covers the base setup of the Ubuntu Server VM that hosts my homelab practice environment and self-hosted tools.

## Initial Setup Steps

1. Installed Ubuntu Server in VirtualBox
2. Created a dedicated non-root user account
3. Updated packages:

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

4. Installed baseline tooling:

   ```bash
   sudo apt install curl git net-tools htop -y
   ```

## Basic Configuration

- Verified network connectivity
- Confirmed SSH and local console access
- Set the timezone
- Checked disk and memory usage
- Tested package management

## Ongoing Use

- Linux administration practice
- Running personal tools and services
- Troubleshooting and system administration learning
