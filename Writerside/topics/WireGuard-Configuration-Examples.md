# WireGuard Configuration Examples

## Example 1
This example is for the most common use case of WireGuard, which is a peer-server configuration. That means peers will tunnel all traffic to the server, then to the Internet, like a commercial available VPN.

First, we will need to know what is our default network interface, the one that is connected to your local network, or publicly.
```bash
iifconfig
```
Then you should see something like this:
```
root@iZxpek3vn1di7xZ:~# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.18.62.60  netmask 255.255.192.0  broadcast 172.18.63.255
        inet6 fe80::216:3eff:fe01:f43c  prefixlen 64  scopeid 0x20<link>
        ether 00:16:3e:01:f4:3c  txqueuelen 1000  (Ethernet)
        RX packets 858900  bytes 668327533 (668.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 673313  bytes 409479887 (409.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 212734  bytes 11607282 (11.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 212734  bytes 11607282 (11.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
...
```

Look for the interface have the IP address you want (`inet`). In my case it would be `eth0`.

Now, we can head to WGDashboard and add a configuration. Feel free to change the **Configuration Name**, **Listen Port** and **IP Address/CIDR** as you want

![](Screenshot 2025-01-19 at 9.29.21 PM.png)

Then we scroll to the bottom and expand **Optional Settings**. To be able to have our peer's traffic go out from the server, we need to setup `iptables` rules. In this example, we will need to set `PostUp` and `PostDown`

### `PostUp`
```Bash
iptables -A FORWARD -i wg0 -j ACCEPT; iptables -A FORWARD -o wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE;
```

### `PostDown`

```Bash
iptables -D FORWARD -i wg0 -j ACCEPT; iptables -D FORWARD -o wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE;
```

<note>
	<b>Please replace <code>wg0</code> in both commands with the Configuration Name you set above, as well as replace `eth0` in both commands with the network interface you got above.</b>
</note>

In my case it will look like this:
![](Screenshot 2025-01-19 at 9.36.03 PM.png)

then click **Save**. Now you can create peers and your traffic should go through your server.