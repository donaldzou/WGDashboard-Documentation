# Update WireGuard Configuration

Update WireGuard configuration information

## Request

`POST /api/updateWireguardConfiguration`

### Body Parameter

```json
{
	"Name": "wg88",
	"Address": "10.24.4.0/23",
	"ListenPort": 56768,
	"PostDown": "iptables -D FORWARD -i wg0 -j ACCEPT; iptables -D FORWARD -o wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o enp0s1 -j MASQUERADE;",
	"PostUp": "iptables -A FORWARD -i wg0 -j ACCEPT; iptables -A FORWARD -o wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o enp0s1 -j MASQUERADE;",
	"PreDown": "",
	"PreUp": ""
}
```

## Response

`200 - OK`

```json
{
    "data": true,
    "message": null,
    "status": true
}
```

If the `Name` provided does not exist or `Name` is not in body parameter

```json
{
    "data": null,
    "message": "Please provide a valid configuration name",
    "status": false
}
```