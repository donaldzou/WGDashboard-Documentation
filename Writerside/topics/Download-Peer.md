# Download Peer

Download Peer's configuration file

## Request

`GET /api/downloadPeer/<configName>?id=`

### Query Parameter

| Parameter | Type   |                                                                                |
|-----------|--------|--------------------------------------------------------------------------------|
| `id`      | string | The `id` of the peer you want to download, which is the Public Key of the peer |

## Response

`200 - OK`

<note>Request Success</note>

If request success, it will return an object inside `data` containing the content of the `.conf` file for this peer as well as the file name for `.conf` file

```json
{
	"data": {
		"file": "[Interface]\nPrivateKey = EB/izbtDPJ/Wk+XBg1+UD10Mt4lL4hkjWLIyw/XL6GY=\nAddress = 10.24.0.4/32\nMTU = 1420\nDNS = 1.1.1.1\n\n[Peer]\nPublicKey = mCP70rKd4iumKptwTgzvAR3g8/D74ZDkwR0EuI10uk4=\nAllowedIPs = 0.0.0.0/0\nEndpoint = 10.0.2.2:56767\nPersistentKeepalive = 21\nPresharedKey = 4ODtONbsAM+HS8Ek9f195vBNVN4w9u4fhO2WqLNr02Q=\n",
		"fileName": "BulkPeer#3_20240918_235236_wg88"
	},
	"message": null,
	"status": true
}
```

<warning>Request Failed</warning>

If configuration does not exist

```json
{
  "data": null,
  "message": "Configuration does not exist",
  "status": false
}
```

If peer does not exist

```json
{
  "data": null,
  "message": "Peer does not exist",
  "status": false
}
```