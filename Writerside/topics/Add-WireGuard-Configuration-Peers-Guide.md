# Add WireGuard Configuration Peers

To add a peer, simply click "+ Peer" button in your configuration

![add-peers-button.png](https://wgdashboard-resources.tor1.cdn.digitaloceanspaces.com/Documentation%20Images/user-guides/add-peers-button.png)

Once you clicked the button, you will see a form similar to adding a configuration, and will need to input the following fields.

- **Name**
  - This is **not a required** field. You can leave it empty to give the peer a name you like.
- **Private Key & Public Key**
  - This is **required** field. Both Private and Public Key will be auto-generated. If you would like to use your own key pair, simply toggle the switch of "Use your own Private and Public Key"
- **Allowed IPs**
  - The IP addresses of this peer. It will be auto-generated with the first available IP Address. You can add more IP Address by clicking "Pick Available IP" button.
  - If you wish to add custom IP Address, you can also type it in the input below.
- **Endpoint Allowed IPs**
  - The IP Address range you want to forward your traffic. For example, if you just want to forward your subnet traffic, you can set it to match configuration's Allowed IPs. 
  - But if you want to forward all traffic through WireGuard, you can set it to `0.0.0.0/0, ::/0`
- **DNS**
  - The DNS servers that this peer will be using.
- **Pre-Shared Key**
  - If you want an extra layer of security between your server and peer, you can toggle this feature to let WireGuard to additional symmetric encryption. 
  - More information: [WireGuard: Next Generation Kernel Network Tunnel, 5.2 - Optional Pre-shared Symmetric Key Mode](https://www.wireguard.com/papers/wireguard.pdf)
- **MTU**
  - [The MTU is automatically determined from the endpoint addresses or the system default route, which is usually a sane choice.](https://github.com/pirate/wireguard-docs?tab=readme-ov-file#MTU)
- **Persistent Keepalive**
  - [If the connection is going from a NAT-ed peer to a public peer, the node behind the NAT must regularly send an outgoing ping in order to keep the bidirectional connection alive in the NAT router's connection table.](https://github.com/pirate/wireguard-docs?tab=readme-ov-file#persistentkeepalive)