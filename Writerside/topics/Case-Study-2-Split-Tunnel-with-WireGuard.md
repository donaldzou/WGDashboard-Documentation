# Case Study #2 - Split Tunnel with WireGuard

## Issue

Some sites are not able to access when WireGuard is connected, and we want to white-list them. 
Currently, we can only control what traffic go through WireGuard, but is difficult to control what don't. Fortunately, we can rely on a project called [Wireproxy](https://github.com/pufferffish/wireproxy).

## Solution

With Wireproxy, we will expose the WireGuard connection as a HTTP/HTTPS proxy, and use a PAC (Proxy Automatic Configuration) file to determine which domain should go through the WireGuard interface. This solution works on both **macOS** and **Windows**, but there might be some difference when setting it up, I will explain it below.

### First Step: WireGuard

WireGuard can be hosted in a server on DigitalOcean like usual, and manage with WGDashboard.

Example:

```ini
[Interface]
PrivateKey = QGA1K4NUMHa7HoYbI7Ppmmo39606xxkepvv0if++x3c=
Address = 10.20.0.1/32
DNS = 8.8.8.8
MTU = 1420

[Peer]
PublicKey = 4y1WQJ7As8Ttmc3nBkESZsaPTogSh/u+SX+ETg1CjCI=
AllowedIPs = 10.20.0.0/24
Endpoint = wg.server:51820
PersistentKeepalive = 21
```

### Second Step: Web Server to host PAC file

We will be using a web server to host the `.pac` file, any web server will be fine. The web server can run on the same server as WireGuard is running. Notice the port must be difference. In this example, the web server is running on port `8080` and the address is`http://192.168.31.65:8080`, then under the web server's directory, create a `.pac` file with any name you want, as long as is easy to remember. I will be using `proxy.pac`

`http://192.168.31.65:8080/proxy.pac`

```javascript
function FindProxyForURL(url,host)
{
    // Access the internet directly for one site
    if (isPlainHostName(host) || dnsDomainIs(host, "www.iplocation.net")) {
        return "DIRECT";
    }
    // Everything else uses a proxy. Note semi-colon delimiter between strings.
    return "PROXY 127.0.0.1:25345";
}
```

In this example, it included a default function required by a PAC file, and in the function, the first `if` statement is determine wheather the `host`(hostname) is a local hostname, **or** the current domain is equal to `www.iplocation.net`, if any of conditions is true (since we are doing `or`), it will return the proxy as `DIRECT`, means no proxy for this trafic, if not, return a proxy setting to `127.0.0.1:25345` (I will explain this below).

### Third Step: Wireproxy on client's device

First we need to download Wireproxy onto client's device, it support macOS (x86/ARM) and Windows (x86), you can find
them here: [](https://github.com/pufferffish/wireproxy/releases/tag/v1.0.9), it is a command line tool and you need to
extract them out of the tarball.

After download, we will need to create a configuration on each employee's device accroding to their WireGuard configuration, based on the tutorial here: [](https://github.com/pufferffish/wireproxy?tab=readme-ov-file#sample-config-file)

`emp1.conf`

```ini
[Interface]
PrivateKey = QGA1K4NUMHa7HoYbI7Ppmmo39606xxkepvv0if++x3c=
Address = 10.20.0.1/32
MTU = 1420
DNS = 8.8.8.8

[Peer]
PublicKey = 4y1WQJ7As8Ttmc3nBkESZsaPTogSh/u+SX+ETg1CjCI=
AllowedIPs = 0.0.0.0/0
Endpoint = 8.134.130.73:51820
PersistentKeepalive = 21

[http]
BindAddress = 127.0.0.1:25345
```

This configuration is not much difference than a regular WireGuard configuration, but it added an aditional section `http` which means it will create a proxy service on `127.0.0.1:25345` , the same one we used in the `.pac` file above.

After saving it, we will now run Wireproxy. Since it is a CLI tool, on macOS we will run it with Terminal, and on Windows we can do PowerShell. What you need to do is `wireproxy -c "configuration_file"`

In this case it would be in macOS

```
./wireproxy -c "emp1.conf"
```

and in Windows

```
./wireproxy.exe -c "emp1.conf"
```

Then you should see bunch of debug output. Now head to the system's proxy settings:

- macOS: Wi-Fi > Details > Proxy > Automatic Proxy Configuration
- Windows: Network and Internet > Proxy > Use Setup Script

And in the URL, type in the URL for your PAC file configured above, in my case it would be `http://192.168.31.65:8080/proxy.pac`

After apply, try to access these two website:

- [](https://whatismyipaddress.com/)
- [](https://www.iplocation.net/)

In the first website, you should see it return your WireGuard's IP and second you should see your original IP, and in that case, which means you're done!