# Get WireGuard Configuration Available IPs

Get a list of available IP address of this WireGuard Configuration

## Request

`GET /api/getAvailableIPs/<configName>`

## Response

`200 - OK`

<note>Request Success</note>

Will return a list of string containing available IP addresses available for this configuration

```json
{
	"data": [
      "10.24.0.121/32",
      "10.24.0.122/32",
      "10.24.0.123/32"
    ],
	"message": null,
	"status": true
}
```