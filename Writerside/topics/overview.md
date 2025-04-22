# 📣 What's New: v4.2.0

<img src="https://wgdashboard-resources.tor1.cdn.digitaloceanspaces.com/Releases/v4.2.0.png" style="block"  alt="" />

## 🎉 New Features
- Since the release of v4.1.0, there are more display languages added by our beloved contributors, and now we have **20** display languages!
    - New display languages:
        - **Arabic** from [@sobhydo](https://github.com/sobhydo)
        - **Belarusian** from [@Bardatsky](https://github.com/Bardatsky)
        - **Farsi** from [@mahdiMGF2](https://github.com/mahdiMGF2)
        - **Japanese** from [@Jumala9163](https://github.com/Jumala9163)
        - **Korean** from [@wdk-kr](https://github.com/wdk-kr)
        - **Thai** from [@karorogunso](https://github.com/karorogunso)
    > If you would like to contribute, please follow the instructions on [Localization of WGDashboard](https://github.com/donaldzou/WGDashboard/issues/397). Thanks in advance!
- **Support AmneziaWG**: Tested with Kernel Version on Ubuntu 22.04 and Go Version on Docker
- **Edit Raw WireGuard Configuration**: You can now edit the configuration file directly from WGDashboard
- **System Status**: You're now able to view your system's CPU / Memory / Disk / Network usage
- **Share Peer w/ Email**: You're now able to connect your email account via SMTP to WGDashboard, visit [](Email-Service.md) for more information
- **Upload Existing Configuration**: You can now upload a `.conf` when creating your configuration
- **Download Backup**

## 🛠️ Some Adjustments
- Added support to Ubuntu 24.10
- UI Adjustments
  - Added Peer's endpoint back to the UI
  - Added tooltips to Peer's dropdown
  - Added dismiss to notification
- API Adjustment: From now on, API Documentation will be hosted on Postman.
  - Adding Peer: It will now generate key / IP address if not provided
- Dropping `ifcfg`

## 🧐 Bugs Fixed
- `auth_req` is not working [#522](https://github.com/donaldzou/WGDashboard/issues/522)
- Accept duplicate entry in WireGuard Configuration due to WireGuard edit the file [#497](https://github.com/donaldzou/WGDashboard/issues/497)
- Backup peers [#332](https://github.com/donaldzou/WGDashboard/issues/322)
- When using `%i` in Post/Pre script will cause Python error [#493](https://github.com/donaldzou/WGDashboard/issues/493)
- And many other bugs...

> I'm planning to take things slow after this update, to think about what's the future about this project and try to make it as stable as possible, while keeping it **simple**.