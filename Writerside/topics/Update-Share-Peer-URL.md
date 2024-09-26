# Update Share Peer URL

Update Share Peer URL's expire date

## Request

`POST /api/sharePeer/update`

### Body Parameter

```json
{
  	"ShareID": "448a6f79-f6fc-4ce9-802a-1a3142ae7253",
  	"ExpireDate": "2024-10-09 23:50:52"
}
```

| Parameter       | Type   |                                                                                                  |
|-----------------|--------|--------------------------------------------------------------------------------------------------|
| `ShareID`       | string | The ShareID you want to update                                                                   |
| `ExpireDate`    | string | Expire date for the URL, format is `YYYY-MM-DD hh\:mm:ss` (24-hours). This field is **optional** |	


## Response

`200 - OK`

<note>Request Success</note>

If create successfully, it will return an object in the data, it contains information about the updated share URL

```json
{
  "data": [
	{
		"Configuration": "wg88",
		"ExpireDate": "2024-10-09 23:50:52",
		"Peer": "72y7R7deXRLZoIb+BYNFWe5RuCmXnWxTSMHfv4Kjay8=",
		"ShareID": "448a6f79-f6fc-4ce9-802a-1a3142ae7253"
	}
  ],
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