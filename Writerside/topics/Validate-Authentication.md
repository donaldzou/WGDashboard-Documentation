# Validate Authentication

This endpoint if needed for non-cross-server access. This will check if the cookie on the client side is still valid on the server side.

#### Request

`GET /api/validateAuthentication`

#### Response

`200 - OK`

Session is still valid

```json
{
    "data": null,
    "message": null,
    "status": true
}
```

Session is invalid

```json
{
    "data": null,
    "message": "Invalid authentication.",
    "status": false
}
```