# Add WGDashboard API Key

Add a new API Key in WGDashboard

## Request

`POST /api/newDashboardAPIKey`

### Body Parameters

```json
{
    "neverExpire": false,
    "ExpiredAt": "2024-12-31 16:00:00"
}
```
| Parameter     | Type   |                                                                                    |
|---------------|--------|------------------------------------------------------------------------------------|
| `neverExpire` | bool   | If this is `false`, please specify a date in `ExpiredAt`                           |
| `ExpiredAt`   | string | If `neverExpire` is `true`, this can be omitted. Format is `YYYY-MM-DD hh\:mm:ss`. |

## Response

`200 - OK`

If success, it will return the latest list of API Keys

```json
{
  "data": [
    {
      "CreatedAt": "2024-08-15 00:42:31",
      "ExpiredAt": null,
      "Key": "AXt1x3TZMukmA-eSnAyESy08I14n20boppSsknHOB-Y"
    },
    {
      "CreatedAt": "2024-08-14 22:50:44",
      "ExpiredAt": "2024-12-31 16:50:43",
      "Key": "ry0Suo0BrypSMzbq0C_TjkEcgrFHHj6UBZGmC2-KI2o"
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