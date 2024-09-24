# Update Peer Settings

Update different settings of existing peer

## Request

`POST /api/updatePeerSettings/<configName>`

### URL Parameter

| Parameter    | Type   |                                   |
|--------------|--------|-----------------------------------|
| `configName` | string | The config name of the peer is in |

### Body Parameter

```json
{
	"DNS": "1.1.1.1",
	"ShareLink": [],
	"allowed_ip": "10.24.0.3/32",
	"configuration": {
		"Address": "10.24.0.0/24",
		"ConnectedPeers": 0,
		"DataUsage": {
			"Receive": 0,
			"Sent": 0,
			"Total": 0
		},
		"ListenPort": "56767",
		"Name": "wg88",
		"PostDown": "",
		"PostUp": "",
		"PreDown": "",
		"PreUp": "",
		"PrivateKey": "WPILUumsSAM6IeQRQj2VnPYAh+6GvFnKqh7fKmWs6EI=",
		"PublicKey": "mCP70rKd4iumKptwTgzvAR3g8/D74ZDkwR0EuI10uk4=",
		"SaveConfig": true,
		"Status": false
	},
	"cumu_data": 0,
	"cumu_receive": 0,
	"cumu_sent": 0,
	"endpoint": "(none)",
	"endpoint_allowed_ip": "0.0.0.0/0",
	"id": "HqcO7P6oLRPYaTCO8iBG/xYJMlSGD1NaMtp6koeY7hA=",
	"jobs": [],
	"keepalive": 21,
	"latest_handshake": "No Handshake",
	"mtu": 1420,
	"name": "Donald's Macbook Pro ",
	"preshared_key": "sHCWzd312NIuNOXyqWwvzBGcYMKPuUmV5s1Qs8wS0kk=",
	"private_key": "CDGt4pjKf3XD1XP65YTy7OFzegshNuKgsk5DO5lu+EM=",
	"remote_endpoint": "10.0.2.2",
	"status": "stopped",
	"total_data": 0,
	"total_receive": 0,
	"total_sent": 0,
	"restricted": false
}
```

## Response

<note>Request Success</note>

If success, it will return the latest list of API Keys after deleting the one you provided

```json
{
  "data": [
	
  ],
  "message": null,
  "status": true
}
```

<warning>Request Failed</warning>

If the Allowed IP provided is taken by another peer

```json
{
    "data": null,
    "message": "Allowed IP already taken by another peer",
    "status": false
}
```

If endpoint allowed IP format is incorrect

```json
{
    "data": null,
    "message": "Endpoint Allowed IPs format is incorrect",
    "status": false
}
```

If DNS format is incorrect

```json
{
    "data": null,
    "message": "DNS format is incorrect",
    "status": false
}
```

If MTU format is not correct

```json
{
    "data": null,
    "message": "MTU format is not correct",
    "status": false
}
```

If Persistent Keepalive format is not correct

```json
{
    "data": null,
    "message": "Persistent Keepalive format is not correct",
    "status": false
}
```

If Private Key does not match with Public Key

```json
{
    "data": null,
    "message": "Private key does not match with the public key",
    "status": false
}
```

If execute `wg set` failed

```json
{
    "data": null,
    "message": "(Error message from wg)",
    "status": false
}
```


