# Get Share Peer URL

Get the share URL for a peer

## Request

`GET /api/sharePeer/get?ShareID=`

### Query Parameter

| Parameter | Type   |                               |
|-----------|--------|-------------------------------|
| `ShareID` | string | The `ShareID` you want to get |

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

If `ShareID` is blank

```json
{
  "data": null,
  "message": "Please specify ShareID",
  "status": false
}
```

If `ShareID` does not exist

```json
{
  "data": null,
  "message": "ShareID does not exist",
  "status": false
}
```