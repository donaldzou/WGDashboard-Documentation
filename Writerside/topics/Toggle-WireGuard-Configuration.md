# Toggle WireGuard Configuration

To turn on/off of a WireGuard Configuration

## Request

`GET /api/toggleWireguardConfiguration/?configurationName=`

### Query String Parameter

| Parameter           | Type   |
|---------------------|--------|
| `configurationName` | string |

## Response

`200 - OK`

If toggle is successful, server will return the current status in `status`: `true` or `false` indicating if the configuration is up or not.

```json
{
    "data": true,
    "message": null,
    "status": true
}
```

If the `configurationName` provided does not exist

```json
{
    "data": null,
    "message": "Please provide a valid configuration name",
    "status": false
}
```