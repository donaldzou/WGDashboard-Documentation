# Get WireGuard Configuration Peers Information

## Request

`GET /api/getWireguardConfigurationInfo?configurationName=`

### Query String Parameter

| Parameter           | Type   |
|---------------------|--------|
| `configurationName` | string |

## Response

`200 - OK`

```json
{
  "data": {
    "configurationInfo": {
      "Address": "10.98.0.0/24",
      "ConnectedPeers": 0,
      "DataUsage": {
        "Receive": 0.00129140168428421,
        "Sent": 0.00821710377931595,
        "Total": 0.00950850546360016
      },
      "ListenPort": "51839",
      "Name": "wg1",
      "PostDown": "iptables -D FORWARD -i wg1 -j ACCEPT; iptables -t nat -D POSTROUTING -o enp0s1 -j MASQUERADE;",
      "PostUp": "iptables -A FORWARD -i wg1 -j ACCEPT; iptables -t nat -A POSTROUTING -o enp0s1 -j MASQUERADE;",
      "PreDown": "",
      "PreUp": "",
      "PrivateKey": "gL1lPwtRlZnHCtkc/RKdlQIrzw4VA7EB7p1cME8Tq3E=",
      "PublicKey": "RTxJqmTUZyyGokWEZL+HKM5aa+MMj7u9rxh0FG22H1o=",
      "SaveConfig": true,
      "Status": true,
      "TotalPeers": 10
    },
    "configurationPeers": [
      {
        "DNS": "1.1.1.1",
        "ShareLink": [],
        "allowed_ip": "10.98.0.2/32",
        "configuration": {
          ...
        },
        "cumu_data": 0,
        "cumu_receive": 0,
        "cumu_sent": 0,
        "endpoint": "192.168.31.124:51938",
        "endpoint_allowed_ip": "0.0.0.0/0",
        "id": "SlDZpaf+aVwqvkKU92PLs5eI6ReHlO6Q0adNlFd9Qzc=",
        "jobs": [],
        "keepalive": 21,
        "latest_handshake": "22:53:35",
        "mtu": 1420,
        "name": "BulkPeer #2_20250104_215907",
        "preshared_key": "",
        "private_key": "SKGMS8Vmh6UFH+T8VSvPSbg83dJVEHK3zQHbbO/uV3s=",
        "remote_endpoint": "wg.local",
        "status": "stopped",
        "total_data": 0.00950850546360016,
        "total_receive": 0.00129140168428421,
        "total_sent": 0.00821710377931595
      },
      ...
    ]
  },
  "message": null,
  "status": true
}
```
