# Traceroute

Traceroute IP address or URL from WGDashboard

## Request

`GET /api/traceroute/execute?ipAddress=`

| Parameter   | Type   |                                  |
|-------------|--------|----------------------------------|
| `ipAddress` | string | The IP address you want to trace |

## Response

`200 - OK`

<note>Request Success</note>

```json
{
	"data": [
		{
			"avg_rtt": 8.239,
			"hop": 1,
			"ip": "192.168.31.1",
			"max_rtt": 9.511,
			"min_rtt": 6.968
		},
		{
			"avg_rtt": 7.943,
			"hop": 2,
			"ip": "192.168.1.1",
			"max_rtt": 9.954,
			"min_rtt": 5.931
		},
		{
			"avg_rtt": 16.254,
			"hop": 3,
			"ip": "10.0.192.1",
			"max_rtt": 17.593,
			"min_rtt": 14.916
		},
	    ...
		{
			"avg_rtt": "*",
			"hop": 19,
			"ip": "*",
			"max_rtt": "*",
			"min_rtt": "*"
		},
		{
			"avg_rtt": 60.567,
			"hop": 20,
			"ip": "20.205.243.166",
			"max_rtt": 60.996,
			"min_rtt": 60.137
		}
	],
	"message": null,
	"status": true
}
```