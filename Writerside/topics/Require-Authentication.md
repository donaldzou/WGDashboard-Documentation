# Require Authentication

This endpoint to check if your WGDashboard require authentication

#### Request

`GET /api/requireAuthentication`

#### Response

`200 - OK`

If required

```json
{
    "data": true,
    "message": null,
    "status": true
}
```

Session is invalid

```json
{
    "data": true,
    "message": null,
    "status": true
}
```