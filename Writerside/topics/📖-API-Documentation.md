# 📖 API Documentation

I'm still updating this documentation. If you have any questions, please don't hesitate to contact me :)

## Get Started

To use the REST API of your WGDashboard, you need to obtain an API Key.

### Create API Key

1. To request an API Key, simply login to your WGDashboard, go to **Settings**, scroll to the very bottom. Click the **switch** on the right to enable API Key.
2. Click the blur **Create** button, set an **expiry date** you want or **never expire**, then click **Done**.

### Use API Key

- Simply add `wg-dashboard-apikey` with the value of your API key into the HTTP Header.

<tabs>
<tab title="Default">
<code-block lang="javascript">
fetch('http://server:10086/api/handshake', {
    headers: {
       'content-type': 'application/json',
        'wg-dashboard-apikey': 'insert your api key here'
    },
    method: "GET"
})
</code-block>
</tab>
<tab title="With APP_PREFIX set">

<note>
For more information, please visit <a href="✂️-Dashboard-Configuration.md"/>
</note>
<br/>

<code-block lang="javascript">
fetch('http://server:10086/[app_prefix]/api/handshake', {
    headers: {
       'content-type': 'application/json',
        'wg-dashboard-apikey': 'insert your api key here'
    },
    method: "GET"
})
</code-block>
</tab>
</tabs>

### Request Method

It will only be `POST` or `GET`

### Endpoint URL Format

There are 2 types of URL format

1. Regular URL
   	- For example: `/api/getWireguardConfigurations`
2. Regular URL with a parameter in the path
   	- For example: `/api/deletePeers/<configName>`.
	- **Currently, `configName` is the only URL parameter. To use it, simply replace it with an existing WireGuard configuration name. Such as `wg0`**