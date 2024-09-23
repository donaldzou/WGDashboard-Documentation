# Get WGDashboard API Keys

Get a list of active API key in WGDashboard

## Request

`GET /api/getDashboardAPIKeys`

## Response

`200 - OK`

If API Key function is enabled and there are active API keys

> If `ExpiredAt` is `null`, that means this API key will never expire
{style=warning}

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
            "ExpiredAt": "2024-08-21 22:50:43",
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