# Update WGDashboard Configuration Item

## Request

`POST /api/updateDashboardConfigurationItem`

### Body Parameters

```json
{
    "section": "Server",
    "key": "dashboard_theme",
    "value": "dark"
}
```
| Parameter | Type   |                                                          |
|-----------|--------|----------------------------------------------------------|
| `section` | string | Each section in the `wg-dashboard.ini`                   |
| `key`     | string | Each key/value pair under each in the `wg-dashboard.ini` |
| `value`   | string | Value for this key/value pair                            |


## Response

`200 - OK`

If update is success

```json
{
    "data": true,
    "message": null,
    "status": true
}
```

If update failed

```json
{
    "data": true,
    "message": "Message related to the error will appear here",
    "status": false
}
```