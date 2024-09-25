# Delete WGDashboard API Key

Delete an existing API Key in WGDashboard

## Request

`POST /api/deleteDashboardAPIKey`

### Body Parameters

```json
{
    "key": "ry0Suo0BrypSMzbq0C_TjkEcgrFHHj6UBZGmC2-KI2o"
}
```
| Parameter | Type   |                                |
|-----------|--------|--------------------------------|
| `key`     | string | The API Key you want to delete |

## Response

`200 - OK`

If success, it will return the latest list of API Keys after deleting the one you provided

```json
{
  "data": [
    {
      "CreatedAt": "2024-08-15 00:42:31",
      "ExpiredAt": null,
      "Key": "AXt1x3TZMukmA-eSnAyESy08I14n20boppSsknHOB-Y"
    }
  ],
  "message": null,
  "status": true
}
```

If API key function is disabled

```json
{
    "data": null,
    "message": "Dashboard API Keys function is disabled",
    "status": false
}
```