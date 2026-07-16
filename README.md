# Homelab / VPS Setup

Infrastructure documentation and runbooks for my self-hosted Ubuntu Server homelab, managed entirely over SSH and Tailscale.

## Overview

This repository documents how I built and operate my personal server environment: an Ubuntu Server VM (VirtualBox) plus VPS-based systems, connected through a Tailscale mesh and administered from the command line over SSH. It doubles as the infrastructure layer for my other projects — the bots and assistant tooling I build run on this server, so keeping it healthy is a real operational responsibility, not just an exercise.

## Architecture

```
Laptop / phone / other devices
        |
        |  Tailscale mesh (WireGuard-based, no public ports)
        v
Ubuntu Server VM (VirtualBox)  <---->  VPS environments
        |
        SSH: all administration is CLI-only, no GUI
```

## Runbooks in This Repo

| Document | Covers |
|---|---|
| [ubuntu-server-setup.md](ubuntu-server-setup.md) | Base OS install, user setup, package updates, baseline tooling |
| [tailscale-setup.md](tailscale-setup.md) | Joining the tailnet, verifying connectivity, why no ports are exposed publicly |
| [ssh-access-workflow.md](ssh-access-workflow.md) | Day-to-day remote administration workflow over SSH |

## Key Skills Demonstrated

- Ubuntu Server administration: users, `apt` package management, timezone, disk and memory checks
- Remote access design: Tailscale (WireGuard-based mesh VPN) instead of public port-forwarding
- SSH-based, GUI-free administration across multiple hosts
- Virtualization with VirtualBox
- Runbook-style documentation so the environment can be rebuilt from scratch

## What I Learned

- **Headless administration is a different skill.** Everything on this server happens over SSH with no desktop to fall back on. That forced me to get fluent with the core CLI toolset — `htop`, `df -h`, `ip a`, `systemctl`, log files — because there is no other way to see what the machine is doing.
- **Don't expose ports you don't have to.** My first instinct for remote access was router port-forwarding. Reading about the attack surface of a public SSH port led me to Tailscale instead: the server is reachable from all my devices but has zero publicly exposed services, which is both safer and simpler to manage.
- **A server you depend on teaches faster than a lab you reset.** Because my other projects actually run on this machine, mistakes have consequences — a bad update or a full disk takes real services down. That changed how carefully I make changes and how quickly I check disk, memory, and connectivity when something feels off.
- **Write the runbook while you build.** The first time I set this environment up, I did it from memory and couldn't have repeated it. These documents exist so the whole environment is reproducible step by step — the same documentation discipline I would want from any IT team I join.
- **Verify each layer after changing it.** After every setup step I confirm the result — package installs, network connectivity, SSH reachability, tailnet visibility — before moving on. Catching a problem at the layer it was introduced is far easier than untangling it three steps later.

---
Built and documented by **Edward J. Penna** — [github.com/wardoep](https://github.com/wardoep)
