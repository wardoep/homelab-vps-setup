# Tailscale Setup

## Purpose

Tailscale provides secure remote access to the homelab server without exposing any ports to the public internet.

## Setup Steps

1. Installed Tailscale on the Ubuntu Server VM
2. Authenticated the device to my tailnet
3. Verified remote connectivity over the tailnet
4. Confirmed the machine could be reached from my other devices

## Benefits

- Secure remote access with no publicly exposed ports or router port-forwarding
- Stable addressing for the server regardless of the local network
- Access to tools running on the server from anywhere

## Notes

- The device stays continuously available through the tailnet
- Used routinely for remote maintenance and troubleshooting
