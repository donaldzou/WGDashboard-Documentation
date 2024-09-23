# Get WireGuard Configurations

To get all WireGuard configurations in `/etc/wireguard`

#### Request

`GET /api/getWireguardConfigurations`

#### Response

`200 - OK`

```json
{
    "data": [
        {
            "Address": "10.200.200.1/24",
            "ConnectedPeers": 0,
            "DataUsage": {
                "Receive": 0.1582,
                "Sent": 2.1012999999999997,
                "Total": 2.2595
            },
            "ListenPort": "51820",
            "Name": "wg0",
            "PostDown": "iptables -D FORWARD -i wg0 -j ACCEPT; iptables -D FORWARD -o wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o enp0s1 -j MASQUERADE;",
            "PostUp": "iptables -A FORWARD -i wg0 -j ACCEPT; iptables -A FORWARD -o wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o enp0s1 -j MASQUERADE;",
            "PreDown": "",
            "PreUp": "",
            "PrivateKey": "8DsSMli3okgUx5frKbFQ0fMW5ZMyqyxOdOW7+g21L18=",
            "PublicKey": "GQlGi8QJ93hWY7L2xlJyh+7S6+ekER9xP11T92T0O0Q=",
            "SaveConfig": true,
            "Status": false
        }
    ],
    "message": null,
    "status": true
}
```