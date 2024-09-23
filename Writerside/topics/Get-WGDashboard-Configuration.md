# Get WGDashboard Configuration

Get the WGDashboard Configuration, such as `dashboard_theme`...

## Request

`GET /api/getDashboardConfiguration`

## Response

`200 - OK`

```json
{
    "data": {
        "Account": {
            "enable_totp": false,
            "password": "some hashed value :(",
            "totp_verified": false,
            "username": "admin"
        },
        "Database": {
            "type": "sqlite"
        },
        "Other": {
            "welcome_session": false
        },
        "Peers": {
            "peer_display_mode": "grid",
            "peer_endpoint_allowed_ip": "0.0.0.0/0",
            "peer_global_dns": "1.1.1.1",
            "peer_keep_alive": "21",
            "peer_mtu": "1420",
            "remote_endpoint": "192.168.2.38"
        },
        "Server": {
            "app_ip": "0.0.0.0",
            "app_port": "10086",
            "app_prefix": "",
            "auth_req": true,
            "dashboard_api_key": true,
            "dashboard_refresh_interval": "5000",
            "dashboard_sort": "status",
            "dashboard_theme": "dark",
            "version": "v4.0",
            "wg_conf_path": "/etc/wireguard"
        }
    },
    "message": null,
    "status": true
}
```