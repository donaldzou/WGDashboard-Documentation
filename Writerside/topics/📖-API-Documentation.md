# 📖 API Documentation

I will try my best to keep this up-to-date :smile:

## Get Started

To use the REST API of your WGDashboard, you need to obtain an API Key.

### Create API Key

1. To request an API Key, simply login to your WGDashboard, go to **Settings**, scroll to the very bottom. Click the **switch** on the right to enable API Key.
2. Click the blur **Create** button, set an **expiry date** you want or **never expire**, then click **Done**.

### Use API Key

- Simply add `wg-dashboard-apikey` with the value of your API key into the HTTP Header.

```javascript
fetch('http://server:10086/api/handshake', {
    headers: {
       'content-type': 'application/json',
        'wg-dashboard-apikey': 'insert your api key here'
    },
    method: "GET"
})
```

## Now you're ready

Please visit this page for details of [](API-Endpoints.md)