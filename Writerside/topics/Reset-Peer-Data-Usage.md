# Reset Peer Data Usage

Reset peer's total, sent or receive data

## Request

`POST /api/resetPeerData/<configName>`

### URL Parameter

| Parameter    | Type   | Description                       |
|--------------|--------|-----------------------------------|
| `configName` | string | The config name of the peer is in |

### Body Parameter

```json
{
  "id": "mCP70rKd4iumKptwTgzvAR3g8/D74ZDkwR0EuI10uk4=",
  "type": "total"
}
```

| Parameter | Type   | Description                                                           |
|-----------|--------|-----------------------------------------------------------------------|
| `id`      | string | Public Key of the peer you want to update                             |
| `type`    | string | Type of data you want to reset. It can be `total`, `receive` or `sent` |

## Response

<note>Request Success</note>

```json
{
  "data": null,
  "message": null,
  "status": true
}
```

<warning>Request Failed</warning>

If `id` is not provided, `configName` does not exist, or peer does not exist

```json
{
  "data": null,
  "message": "Configuration/Peer does not exist",
  "status": false
}
```