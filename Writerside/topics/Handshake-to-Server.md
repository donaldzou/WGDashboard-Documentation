# Handshake to Server

This endpoint is designed for a simple handshake when using API key to connect.

## Request

`GET /api/handshake`

## Response

`200 - OK`

```json
{
    "data": null,
    "message": null,
    "status": true
}
```

`401 - UNAUTHORIZED`

```json
{
    "data": null,
    "message": "Unauthorized access.",
    "status": false
}
```
> Notice: this `401` response will return at all endpoint if your API Key or session is invalid.