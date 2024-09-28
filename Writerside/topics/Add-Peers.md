# Add Peers

Add peers individually or by bulk

## Request

`POST /api/addPeers/<configName>`

### Body Parameter

#### Add peer individually

```json
{
	"name": "Donald's Macbook Pro 123",
	"allowed_ips": [
		"10.24.0.100/32"
	],
	"private_key": "IHYNm6VWb1kV/h4M6xthkgJYOpvGOKbpI24QC1Qt9mU=",
	"public_key": "fzjbAZOtJAQc8uyRBTjvPBTYuaW96bYEHC5TeFResRE=",
	"preshared_key": "Fwgw5H8xenVgyqOVr/rVEIy+vBi2nNiybjXiP45S5Rw=",
	"DNS": "1.1.1.1",
	"endpoint_allowed_ip": "0.0.0.0/0",
	"keepalive": 21,
	"mtu": 1420
}
```

| Parameter             | Type         |                                                      |                                                                                                |
|-----------------------|--------------|------------------------------------------------------|------------------------------------------------------------------------------------------------|
| `allowed_ips`         | list[string] | List of string containing IP address of this peer    |                                                                                                |
| `public_key`          | string       | Public Key of this new peer                          |                                                                                                |
| `private_key`         | string       | Private Key of this new peer                         | Optional, download and QR code not available if not provided                                   |
| `name`                | string       | Name of the peer                                     | Optional                                                                                       |
| `preshared_key`       | string       | Preshared Key of this new peer                       | Optional                                                                                       |
| `DNS`                 | string       | DNS address of this new peer will use when connected | Optional, will use [`peer_global_dns`](✂️-Dashboard-Configuration.md) if not provided          |
| `endpoint_allowed_ip` | string       | Endpoint Allowed IP of this new peer                 | Optional, will use [`peer_endpoint_allowed_ip`](✂️-Dashboard-Configuration.md) if not provided |
| `keepalive`           | int          | Keepalive of this new peer                           | Optional, will use [`peer_keep_alive`](✂️-Dashboard-Configuration.md) if not provided          |
| `mtu`                 | int          | MTU (Max Transmission Unit) of this new peer         | Optional, will use [`peer_mtu`](✂️-Dashboard-Configuration.md) if not provided                 |

#### Add peers in bulk

```json
{
	"bulkAdd": true,
	"bulkAddAmount": 2,
  	"preshared_key_bulkAdd": true,
	"DNS": "1.1.1.1",
	"endpoint_allowed_ip": "0.0.0.0/0",
	"keepalive": 21,
	"mtu": 1420
}
```

| Parameter                | Type   |                                                          |                                                                                                |
|--------------------------|--------|----------------------------------------------------------|------------------------------------------------------------------------------------------------|
| `bulkAdd`                | bool   | Indicate if you want to add peers in bulk                |                                                                                                |
| `bulkAddAmount`          | int    | How many peers you want to add                           |                                                                                                |
| `preshared_key_bulkAdd`  | bool   | Indicate if you want to use Preshared Key for each peers |                                                                                                |
| `DNS`                    | string | DNS address of this new peer will use when connected     | Optional, will use [`peer_global_dns`](✂️-Dashboard-Configuration.md) if not provided          |
| `endpoint_allowed_ip`    | string | Endpoint Allowed IP of this new peer                     | Optional, will use [`peer_endpoint_allowed_ip`](✂️-Dashboard-Configuration.md) if not provided |
| `keepalive`              | int    | Keepalive of this new peer                               | Optional, will use [`peer_keep_alive`](✂️-Dashboard-Configuration.md) if not provided          |
| `mtu`                    | int    | MTU (Max Transmission Unit) of this new peer             | Optional, will use [`peer_mtu`](✂️-Dashboard-Configuration.md) if not provided                 |


## Response

`200 - OK`

<note>Request Success</note>

```json
{
  "data": null,
  "message": null,
  "status": true
}
```

<warning>Request Failed</warning>

When `bulkAddAmount` is more than available IP

```json
{
  "data": null,
  "message": "The maximum number of peers can add is 5",
  "status": false
}
```

If no more available IP when adding by bulk

```json
{
  "data": null,
  "message": "No more available IP can assign",
  "status": false
}
```

If `bulkAddAmount` did not specify or less than 0 when adding by bulk

```json
{
  "data": null,
  "message": "Please specify amount of peers you want to add",
  "status": false
}
```

If `allowed_ips` or `public_key` not provided when adding peer individually

```json
{
  "data": null,
  "message": "Please provide at lease public_key and allowed_ips",
  "status": false
}
```

Configuration does not exist

```json
{
  "data": null,
  "message": "Configuration does not exist",
  "status": false
}
```

Some other unknown issue

```json
{
  "data": "Issue",
  "message": "Add peers failed. Please see data for specific issue",
  "status": false
}
```