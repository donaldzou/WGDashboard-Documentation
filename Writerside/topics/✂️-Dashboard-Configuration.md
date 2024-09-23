# ✂️ Configure

## Configuration File

Since version 2.0, WGDashboard will be using a configuration file called `wg-dashboard.ini`, (It will generate automatically after first time running the dashboard). More options will include in future versions, and for now it included the following configurations:

|                              | Description                                                                                                                                                                                              | Default                                              |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| **`[Account]`**              | *Configuration on account*                                                                                                                                                                               |                                                      |
| `username`                   | Dashboard login username                                                                                                                                                                                 | `admin`                                              |
| `password`                   | Password, will be hash with SHA256                                                                                                                                                                       | `admin` hashed in SHA256                             |
|                              |                                                                                                                                                                                                          |                                                      |
| **`[Server]`**               | *Configuration on dashboard*                                                                                                                                                                             |                                                      |
| `wg_conf_path`               | The path of all the Wireguard configurations                                                                                                                                                             | `/etc/wireguard`                                     |
| `app_ip`                     | IP address the dashboard will run with                                                                                                                                                                   | `0.0.0.0`                                            |
| `app_port`                   | Port the the dashboard will run with                                                                                                                                                                     | `10086`                                              |
| `auth_req`                   | Does the dashboard need authentication to access, if `auth_req = false` , user will not be access the **Setting** tab due to security consideration. **User can only edit the file directly in system**. | `true`                                               |
| `version`                    | Dashboard Version                                                                                                                                                                                        | `v4.0`                                               |
| `dashboard_refresh_interval` | How frequent the dashboard will refresh on the configuration page                                                                                                                                        | `60000ms`                                            |
| `dashboard_sort`             | How configuration is sorting                                                                                                                                                                             | `status`                                             |
| `dashboard_theme`            | Dashboard Theme                                                                                                                                                                                          | `dark`                                               |
| `dashboard_api_key`          | WGDashboard API Key Function                                                                                                                                                                             | `false`                                              |
| `dashboard_language`         | WGDashboard Language                                                                                                                                                                                     | `en`                                                 |
|                              |                                                                                                                                                                                                          |                                                      |
| **`[Peers]`**                | *Default Settings on a new peer*                                                                                                                                                                         |                                                      |
| `peer_global_dns`            | DNS Server                                                                                                                                                                                               | `1.1.1.1`                                            |
| `peer_endpoint_allowed_ip`   | Endpoint Allowed IP                                                                                                                                                                                      | `0.0.0.0/0`                                          |
| `peer_display_mode`          | How peer will display                                                                                                                                                                                    | `grid`                                               |
| `remote_endpoint`            | Remote Endpoint (i.e where your peers will connect to)                                                                                                                                                   | *depends on your server's default network interface* |
| `peer_mtu`                   | Maximum Transmit Unit                                                                                                                                                                                    | `1420`                                               |
| `peer_keep_alive`            | Keep Alive                                                                                                                                                                                               | `21`                                                 |

## Generating QR code and peer configuration file (.conf)

Starting version 2.2, dashboard can now generate QR code and configuration file for each peer. Here is a template of what each QR code encoded with and the same content will be inside the file:

```ini
[Interface]
PrivateKey = QWERTYUIOPO234567890YUSDAKFH10E1B12JE129U21=
Address = 0.0.0.0/32
DNS = 1.1.1.1

[Peer]
PublicKey = QWERTYUIOPO234567890YUSDAKFH10E1B12JE129U21=
AllowedIPs = 0.0.0.0/0
Endpoint = 0.0.0.0:51820
PresharedKey = QWERTYUIOPO234567890YUSDAKFH10E1B12JE129U21=
```

|                   | Description                                                                                            | Default Value                                                                                   | Available in Peer setting |
|-------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------|
| **`[Interface]`** |                                                                                                        |                                                                                                 |                           |
| `PrivateKey`      | The private key of this peer                                                                           | Private key generated by WireGuard (`wg genkey`) or provided by user                            | Yes                       |
| `Address`         | The `allowed_ips` of your peer                                                                         | N/A                                                                                             | Yes                       |
| `DNS`             | The DNS server your peer will use                                                                      | `1.1.1.1` - Cloud flare DNS, you can change it when you adding the peer or in the peer setting. | Yes                       |
| **`[Peer]`**      |                                                                                                        |                                                                                                 |                           |
| `PublicKey`       | The public key of your server                                                                          | N/A                                                                                             | No                        |
| `AllowedIPs`      | IP ranges for which a peer will route traffic                                                          | `0.0.0.0/0` - Indicated a default route to send all internet and VPN traffic through that peer. | Yes                       |
| `Endpoint`        | Your wireguard server ip and port, the dashboard will search for your server's default interface's ip. | `<your server default interface ip>:<listen port>`                                              | Yes                       |
| `PresharedKey`    | The Pre-Shared Key of this peer _(if available)_                                                       | N/A                                                                                             | Yes                       |
