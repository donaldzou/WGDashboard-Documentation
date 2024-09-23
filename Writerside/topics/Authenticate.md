# Authenticate

This endpoint is dedicated for non-cross-server access. It is used to authenticate user's username, password and TOTP

## Request

`POST /api/authenticate`

### Body Parameters

```json
{
    "username": "admin",
    "password": "admin",
    "totp": "123456"
}
```

| Parameter  | Type   |   
|------------|--------|   
| `username` | string |   
| `password` | string |   
| `totp`     | string |   


## Response

`200 - OK`

If username, password and TOTP matched

```json
{
    "data": null,
    "message": null,
    "status": true
}
```

If username, password or TOTP is not match

```json
{
    "data": null,
    "message": "Sorry, your username, password or OTP is incorrect.",
    "status": false
}
```