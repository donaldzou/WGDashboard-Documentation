# Get Peer Schedule Job Logs

Get logs of peer schedule job

## Request

`GET /api/getPeerScheduleJobLogs/<configName>`

## Response

<note>Request Success</note>

```json
{
	"data": [
		{
			"JobID": "11f21ed7-1602-4fac-9dcc-ddf89f9fb967",
			"LogDate": "2024-09-29 08:47:30",
			"LogID": "c8e5c633-75c2-4d6e-9d9f-1134e00887af",
			"Message": "Job is removed due to being deleted or finshed.",
			"Status": "1"
		},
		{
			"JobID": "d66d3f41-c0ec-48ef-a2b7-cbb74e58263f",
			"LogDate": "2024-09-29 07:59:37",
			"LogID": "ecf89cbc-e24c-45c5-aad6-a97cac5d8698",
			"Message": "Job is created if total_data lgt 32 then restrict",
			"Status": "1"
		},
		{
			"JobID": "11f21ed7-1602-4fac-9dcc-ddf89f9fb967",
			"LogDate": "2024-09-29 07:50:24",
			"LogID": "546c1bb4-1c41-41b4-8080-76d383cb22f2",
			"Message": "Job is created if total_data lgt 2 then restrict",
			"Status": "1"
		},
		{
			"JobID": "0ea8b2b5-e024-4e2e-ae69-3118b946b541",
			"LogDate": "2024-09-22 12:59:48",
			"LogID": "c9df4ac1-69b5-4803-9295-fe25af013836",
			"Message": "Job is removed due to being deleted or finshed.",
			"Status": "1"
		},
		{
			"JobID": "0ea8b2b5-e024-4e2e-ae69-3118b946b541",
			"LogDate": "2024-09-22 12:59:29",
			"LogID": "673dcc15-f1b3-417f-9283-7e6c5eb6f83d",
			"Message": "Job is updated from if total_data lgt 3 then restrict; to if total_data lgt 3 then restrict",
			"Status": "1"
		},
		{
			"JobID": "0ea8b2b5-e024-4e2e-ae69-3118b946b541",
			"LogDate": "2024-09-22 12:55:52",
			"LogID": "74e07776-63d7-4c01-8ffe-3b091ddb4fbe",
			"Message": "Job is created if total_data lgt 3 then restrict",
			"Status": "1"
		}
	],
	"message": null,
	"status": true
}
```
