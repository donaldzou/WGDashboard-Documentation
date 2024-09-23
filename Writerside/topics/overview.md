# 📣 What's New: v4.0

> [📹 Demo video on YouTube](https://www.youtube.com/watch?v=0mwzd5Gr2eU)

## 🎉 New Features
- **Updated dashboard design**: Re-designed some of the section with more modern style and layout, the UI is faster and more responsive, it also uses less memory. But overall is still the same dashboard you're familiarized.
- **Docker Solution**: We now have 2 docker solutions! Thanks to @DaanSelen & @shuricksumy for providing them. For more information, please see the [](🐬-Docker-Solutions.md) section.
- **Peer Job Scheduler**: Now you can schedule jobs for each peer to either **restrict** or **delete** the peer if the peer's total / upload / download data usage exceeded a limit, or you can set a specific datetime to restrict or delete the peer.
- **Share Peer's QR Code with Public Link**: You can share a peer's QR code and `.conf` file without the need to loging in.
- **WGDashboard's REST API**: You can now request all the api endpoint used in the dashboard. For more details please review the [](📖-API-Documentation.md).
- **Logging**: Dashboard will now log all activity on the dashboard and API requests.
- **Time-Based One-Time Password (TOTP)**: You can enable this function to add one more layer of security, and generate the TOTP with your choice of authenticator.
- **Designs**
    - **Real-time Graphs**: You can view real-time data changes with graphs in each configuration.
    - **Night mode**: You know what that means, it avoids bugs ;)
- **Enforce Python Virtual Environment**: I noticed newer Python version (3.12) does not allow to install packages globally, and plus I think is a good idea to use venv.

## 🧐 Other Changes
- **Deprecated jQuery from the project, and migrated and rewrote the whole front-end with Vue.js. This allows the dashboard is future proofed, and potential cross server access with a desktop app.**
- Rewrote the backend into a REST API structure
- Improved SQL query efficient
- Removed all templates, except for `index.html` where it will load the Vue.js app.
- Parsing names in `.conf`
- Minimized the need to read `.conf`, only when any `.conf` is modified

## 🥘 New Experimental Features
- **Cross-Server Access**: Now you can access other servers that installed `v4` of WGDashboard through API key.
- **Desktop App**: Thanks to **Cross-Server Access**, you can now download an ElectronJS based desktop app of WGDashboard, and use that to access WGDashboard on different servers.
- > For more information, please visit [](ex)