# Create Share Peer URL

Create a URL to share peer's configuration file and QR Code

## Request

`POST /api/sharePeer/create`

### URL Parameter

| Parameter | Type   |                                   |
|-----------|--------|-----------------------------------|
| ``        | string | The config name of the peer is in |

### Body Parameter

```json
{
   	"Configuration": "wg0",
  	"Peer": "mCP70rKd4iumKptwTgzvAR3g8/D74ZDkwR0EuI10uk4=",
  	"ExpireDate": "2024-10-01 23:50:52"
}
```

| Parameter       | Type   |                                                                     |
|-----------------|--------|---------------------------------------------------------------------|
| `Configuration` | string | The config name of the peer is in                                   |
| `Peer`          | string | The peer you want to share                                          |
| `ExpireDate`    | string | Expire date for the URL, format is `YYYY-MM-DD hh:mm:ss` (24-hours) |	

## Response

<note>Request Success</note>

If create successfully, it will return an object in the data, it contains information about the share URL

```json
{
	"data": [
		{
		  "Configuration": "wg88",
		  "ExpireDate": "2024-10-01 23:50:52",
		  "Peer": "72y7R7deXRLZoIb+BYNFWe5RuCmXnWxTSMHfv4Kjay8=",
		  "ShareID": "448a6f79-f6fc-4ce9-802a-1a3142ae7253"
		}
	],
	"message": null,
	"status": true
}
```

<warning>Request Failed</warning>

If `Configuration` or `Peer` did not provide

```json
{
  "data": null,
  "message": "Please specify configuration and peers",
  "status": false
}
```

If this peer have an existing URL

```json
{
  "data": null,
  "message": "This peer is already sharing, please stop sharing first.",
  "status": false
}
```