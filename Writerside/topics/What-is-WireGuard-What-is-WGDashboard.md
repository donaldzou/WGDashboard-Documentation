# What is WireGuard &amp; What is WGDashboard?

## Overview
WireGuard and WGDashboard are often used together, but they serve different purposes. This article highlights their differences and provides guidance for WGDashboard users who may need help with their WireGuard setup.

---

## What is WireGuard?
[WireGuard](https://www.wireguard.com/) is a simple, high-performance VPN protocol that aims to provide an efficient and secure alternative to traditional VPN protocols. **Key features** of WireGuard include:
- **Speed and Efficiency**: Designed for minimal configuration and high performance.
- **Modern Cryptography**: Utilizes state-of-the-art encryption for enhanced security.
- **Core VPN Functionality**: Provides the VPN tunnel but lacks a user interface or built-in peer management.

---

## What is WGDashboard?
[WGDashboard](https://donaldzou.github.io/WGDashboard-Documentation/) is a **web-based management tool** specifically designed to enhance WireGuard’s usability by providing a graphical user interface (GUI) for configuring and monitoring peers.

<video src="https://www.youtube.com/watch?v=0mwzd5Gr2eU"/>

- Automatically look for existing WireGuard configuration under `/etc/wireguard`
- Easy to use interface, provided credential and TOTP protection to the dashboard
- Manage peers and configuration
	- Add Peers or by bulk with auto-generated information
	- Edit peer information
	- Delete peers with ease
	- Restrict peers
	- Generate QR Code and `.conf` file for peers, share it through a public link
	- Schedule jobs to delete / restrict peer when conditions are met
- View real time peer status
- Testing tool: Ping and Traceroute to your peer

### Important Note for Users
> **WireGuard and WGDashboard are separate components**:
> - **WireGuard** is the VPN software itself.
> - **WGDashboard** is an optional tool for managing and monitoring WireGuard configurations.

If you encounter issues specifically with **WireGuard** (e.g., connectivity or tunnel errors), refer to WireGuard’s [official documentation](https://www.wireguard.com/) or support. 

**WGDashboard** issues related to the interface, peer management, or dashboard functionality can be reported [here](https://github.com/donaldzou/WGDashboard).

---

# Default WireGuard Configuration

A default configuration file (`wg0.conf`) is already included in the standard installation. This configuration is designed to simplify the setup and enhance understanding for new users. You can view and edit it using:

```bash
nano /etc/wireguard/wg0.conf
```

The default configuration looks similar to the following:
```bash
[Interface]
PrivateKey = <your-private-key>
Address = 10.0.0.1/24
SaveConfig = true
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -A FORWARD -o wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE;
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -D FORWARD -o wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE;
ListenPort = 51820
```