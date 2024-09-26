# Delete Peers

To delete peers individually or in bulk

## Request

`POST /api/deletePeers/<configName>`

### Body Parameter

```json
{
  "peers": [
    "mCP70rKd4iumKptwTgzvAR3g8/D74ZDkwR0EuI10uk4=",
    "lKptwTgzvAR3gmCP70rKd4iu8/D74ZDkwR0EuI10uk4=",
    "pCP70rKd4iumK0uk4ptwTgzvAR3g8/D74ZDkwR0EuI1="
  ]
}
```

| Parameter | Type         |                                                          |
|-----------|--------------|----------------------------------------------------------|
| `peers`   | list[string] | List of strings contain public key(s) you want to delete |

## Response

`200 - OK`

<note>Request Success</note>

```json
{
  "data": null,
  "message": "Deleted 3 peer(s)",
  "status": true
}
```

<warning>Request Failed</warning>

If configuration name provided in `configName` does not exist

```json
{
  "data": null,
  "message": "Configuration does not exist",
  "status": false
}
```

If length of `peers` is 0

```json
{
  "data": null,
  "message": "Please specify one or more peers",
  "status": false
}
```

If failed to save to WireGuard

```json
{
  "data": null,
  "message": "Failed to save configuration through WireGuard",
  "status": false
}
```

If failed delete some of the peers

```json
{
  "data": null,
  "message": "Deleted 3 peer(s) successfully. Failed to delete 1 peer(s)",
  "status": false
}
```