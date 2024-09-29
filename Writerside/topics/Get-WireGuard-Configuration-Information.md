# Get WireGuard Configuration Information

Get information about a WireGuard configuration

## Request

`GET /api/getWireguardConfigurationInfo?configurationName=`

### URL Parameter

| Parameter           | Type   |                    |
|---------------------|--------|--------------------|
| `configurationName` | string | Configuration name |

## Response

`200 - OK`

<note>Request Success</note>

```json
{
	"data": {
		"configurationInfo": {
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
			"Status": true
		},
		"configurationPeers": [
			{
				"DNS": "1.1.1.1",
				"ShareLink": [],
				"allowed_ip": "10.24.0.15/32, 10.24.0.19/32",
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
					"Status": true
				},
				"cumu_data": 0,
				"cumu_receive": 0,
				"cumu_sent": 0,
				"endpoint": "(none)",
				"endpoint_allowed_ip": "0.0.0.0/0",
				"id": "YI5GNeKSeiMd1mmZKqWo9RDUIB4Ao3IfGdoDeguAUR4=",
				"jobs": [],
				"keepalive": 21,
				"latest_handshake": "No Handshake",
				"mtu": 1420,
				"name": "Donald's Macbook Pro",
				"preshared_key": "Fwgw5H8xenVgyqOVr/rVEIy+vBi2nNiybjXiP45S5Rw=",
				"private_key": "mBu9sGwXB5KTJHYJ1MTxPdn0oCXnqsC+csZ+E8w1FkU=",
				"remote_endpoint": "10.0.2.2",
				"status": "stopped",
				"total_data": 0,
				"total_receive": 0,
				"total_sent": 0
			}
		],
		"configurationRestrictedPeers": [
			{
			"DNS": "1.1.1.1",
			"ShareLink": [],
			"allowed_ip": "10.24.0.100/32",
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
				"Status": true
			},
			"cumu_data": 0,
			"cumu_receive": 0,
			"cumu_sent": 0,
			"endpoint": "(none)",
			"endpoint_allowed_ip": "0.0.0.0/0",
			"id": "fzjbAZOtJAQc8uyRBTjvPBTYuaW96bYEHC5TeFResRE=",
			"jobs": [],
			"keepalive": 21,
			"latest_handshake": "No Handshake",
			"mtu": 1420,
			"name": "Restricted Peer",
			"preshared_key": "Fwgw5H8xenVgyqOVr/rVEIy+vBi2nNiybjXiP45S5Rw=",
			"private_key": "IHYNm6VWb1kV/h4M6xthkgJYOpvGOKbpI24QC1Qt9mU=",
			"remote_endpoint": "10.0.2.2",
			"status": "stopped",
			"total_data": 0,
			"total_receive": 0,
			"total_sent": 0
			}
		]
	},
	"message": null,
	"status": true
}
```

<warning>Request Failed</warning>

Description

```json
{
  "data": null,
  "message": null,
  "status": true
}
```