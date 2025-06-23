# Case Study #1.1 - Multi-Hop and Hop Again Connection

## Issue

<img src="https://wgdashboard-resources.tor1.cdn.digitaloceanspaces.com/Documentation%20Images/case-study/CaseStudy1-Page-2.drawio.png" alt="" />

So it got me thinking, is it possible to forward the client traffic as many as possible? I think so!

## Solution

> Solution originated from this [Reddit Post](https://www.reddit.com/r/WireGuard/comments/1dn9gxd/help_in_setting_up_multihop_wireguard_tunneling/)

### Specification

| Device   | OS           | WireGuard IP |
|----------|--------------|--------------|
| Client   | iOS          | `10.23.0.1`  |
| Server A | Ubuntu 24.04 | `10.23.0.2`  |
| Server B | Ubuntu 24.04 | `10.23.0.3`  |
| Server C | Ubuntu 24.04 | `10.23.0.4`  |

### Configurations

#### Client

```ini
[Interface]
PrivateKey = <Client_Private_Key>
Address = 10.23.0.1/32
DNS = 1.1.1.1
MTU = 1420

[Peer]
PublicKey = <Server_A_Public_Key>
AllowedIPs = 0.0.0.0/0
Endpoint = ServerA_Public_IP:51830
PersistentKeepalive = 21
```

#### Server A

```Ini
[Interface]
Address = 10.23.0.2/24
SaveConfig = true
PostUp = ip rule add from 10.23.0.0/24 lookup 789
PostUp = ip rule add iif %i table 789 priority 456
PostUp = iptables -A FORWARD -i %i -j ACCEPT
PostUp = iptables -t nat -A POSTROUTING -o %i -j MASQUERADE
PostUp = ip route replace 10.23.0.0/24 dev %i
PreDown = ip route del 10.23.0.0/24 dev %i
PostDown = ip rule del from 10.23.0.0/24 lookup 789
PostDown = ip rule del iif %i table 789 priority 456
PostDown = iptables -D FORWARD -i %i -j ACCEPT
PostDown = iptables -t nat -D POSTROUTING -o %i -j MASQUERADE
ListenPort = 51830
PrivateKey = <Server_A_Private_Key>

[Peer]
PublicKey = <Client_Public_Key>
AllowedIPs = 10.23.0.1/32

[Peer]
PublicKey = <Server_B_Public_Key>
AllowedIPs = 0.0.0.0/0
Endpoint = <Server_B_Public_IP>:51830
```

#### Server B

```Ini
[Interface]
Address = 10.23.0.3/32
SaveConfig = true
PostUp = ip rule add from 10.23.0.0/24 lookup 789
PostUp = ip rule add iif %i table 789 priority 456
PostUp = iptables -A FORWARD -i %i -j ACCEPT
PostUp = iptables -t nat -A POSTROUTING -o %i -j MASQUERADE
PostUp = ip route replace 10.23.0.0/24 dev %i
PreDown = ip route del 10.23.0.0/24 dev %i
PostDown = ip rule del from 10.23.0.0/24 lookup 789
PostDown = ip rule del iif %i table 789 priority 456
PostDown = iptables -D FORWARD -i %i -j ACCEPT
PostDown = iptables -t nat -D POSTROUTING -o %i -j MASQUERADE
ListenPort = 51830
FwMark = 0xca6c
PrivateKey = <Server_B_Private_Key>

[Peer]
PublicKey = <Server_C_Public_Key>
AllowedIPs = 0.0.0.0/0

[Peer]
PublicKey = <Server_A_Public_Key>
AllowedIPs = 10.23.0.2/32
Endpoint = <Server_A_Public_IP>:51830
```

#### Server C

```Ini
[Interface]
Address = 10.23.0.4/32
SaveConfig = true
PreUp =
PostUp = iptables -A FORWARD -i wg1 -j ACCEPT; iptables -A FORWARD -o wg1 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE;
PreDown =
PostDown = iptables -D FORWARD -i wg1 -j ACCEPT; iptables -D FORWARD -o wg1 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE;
ListenPort = 51821
PrivateKey = <Server_C_Private_Key>

[Peer]
PublicKey = <Server_B_Public_Key>
AllowedIPs = 10.23.0.3/32
Endpoint = <Server_B_Public_IP>:51830
PersistentKeepalive = 25
```

## Result

```
donaldzou@Mac ~ % traceroute mirrors.aliyun.com
traceroute to mirrors.aliyun.com.w.alikunlun.com (128.1.157.225), 64 hops max, 40 byte packets
 1  10.23.0.2 (10.23.0.2)  2.688 ms  1.842 ms  1.973 ms
 2  10.23.0.3 (10.23.0.3)  7.848 ms  4.327 ms  4.764 ms
 3  10.23.0.4 (10.23.0.4)  6.558 ms  4.065 ms  3.166 ms
 4  192.168.31.1 (192.168.31.1)  79.309 ms  103.231 ms  10.915 ms
 5  192.168.1.1 (192.168.1.1)  9.070 ms  20.230 ms  69.802 ms
 6  10.1.64.1 (10.1.64.1)  17.966 ms  17.124 ms  14.593 ms
 7  111.23.186.137 (111.23.186.137)  12.987 ms  18.292 ms  20.037 ms
```

As we can see, the traffic went from client to `10.23.0.2` to `10.23.0.3`, then to `10.23.0.4` then to the internet.