# Save Peer Schedule Job

Save peer schedule job

## Request

`POST /api/savePeerScheduleJob/`

### Body Parameter

```json
{
	"Job": {
		"JobID": "11f21ed7-1602-4fac-9dcc-ddf89f9fb967",
		"Configuration": "wg88",
		"Peer": "YI5GNeKSeiMd1mmZKqWo9RDUIB4Ao3IfGdoDeguAUR4=",
		"Field": "total_data",
		"Operator": "lgt",
		"Value": "2",
		"CreationDate": "",
		"ExpireDate": "",
		"Action": "restrict"
	}
}
```

<note>Request Success</note>

```json
{
	"data": [
		{
			"Action": "restrict",
			"Configuration": "wg88",
			"CreationDate": "2024-09-29 07:59:37",
			"ExpireDate": null,
			"Field": "total_data",
			"JobID": "d66d3f41-c0ec-48ef-a2b7-cbb74e58263f",
			"Operator": "lgt",
			"Peer": "YI5GNeKSeiMd1mmZKqWo9RDUIB4Ao3IfGdoDeguAUR4=",
			"Value": "32"
		}
	],
	"message": null,
	"status": true
}
```

<warning>Request Failed</warning>

If `Job` is blank

```json
{
  "data": null,
  "message": "Please specify job",
  "status": false
}
```

If `Configuration` does not exist

```json
{
  "data": null,
  "message": "Please specify peer and configuration",
  "status": false
}
```

If `Please specify peer and configuration` does not exist

```json
{
  "data": null,
  "message": "Peer does not exist",
  "status": false
}
```