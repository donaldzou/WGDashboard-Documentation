# 📣 What's New: v4.1

<video src="https://www.youtube.com/watch?v=0mwzd5Gr2eU"/>
## 🎉 New Features
- **Multi-Language Support**: Now WGDashboard support the following languages on its user interface, big thanks to our user's contribution!
  - **Chinese Traditional**
  - **Chinese Simplified**
  - **Czech** (@jursed)
  - **Dutch** (@DaanSelen)
  - **English**
  - **German** (@orangeferdi)
  - **Italian** (@3vis97)
  - **Russian** (Pixnet)
  - **Ukrainian** (@shuricksumy)

> If you would like to contribute, please follow the instructions on [Localization of WGDashboard](https://github.com/donaldzou/WGDashboard/issues/397). Thanks in advance!

- **Backup & Restore WireGuard Configurations**: Now you can back up your configurations, restore it after a change made to the configuration. **You can also restore it even after deletion.**
- **Delete & Rename WireGuard Configuration:** Now you can delete and rename configuration within WGDashboard
- **Toggle WireGuard Configuration After Startup:** Now you can set WireGuard configurations to be turned on after starting WGDashboard in **Settings**
- **Delete & Download Peers in bulk**
- **Frontend Display of Peer's Configuration File**
- **Added Support on AlmaLinux and Pi OS**
- **Added OpenStreetMap on Ping and Traceroute Tool**

## 🛠️ Some Adjustments
- **Updated Docker configuration**
- **Updates on API endpoints**
- UI Adjustments
- Added version number in navbar
- Added WGDashboard host and port settings
- Added peer delete confirmation
- Added domain support in DNS field for peers

## 🧐 Bugs Fixed
- Mobile UI issues in #353
- Removed WireGuard configuration error alert from Gunicorn start in #328
- Sometimes restrict peer might not be success in #357
- Weird SQLite error causing WGDashboard to crash in #366

## 🗂️ User Guides
Will continue to finish the [](User-Guides.md) sections

## 🥘 Experimental Features
- **Cross-Server Access**: Now you can access other servers that installed `v4` of WGDashboard through API key.
- **Desktop App**: Thanks to **Cross-Server Access**, you can now download an ElectronJS based desktop app of WGDashboard, and use that to access WGDashboard on different servers.
> For more information, please visit [](🥘-Experimental-Features.md)