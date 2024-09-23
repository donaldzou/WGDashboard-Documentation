# Add WireGuard Configuration

Add a new WireGuard Configuration

## Request

`POST /api/addWireguardConfiguration`

### Body Parameters

```json
{
    "ConfigurationName": "wg0",
    "Address": "10.0.0.1/24",
    "ListenPort":  51820,
    "PrivateKey": "eJuuamCgakVs2xUZGHh/g7C6Oy89JGh7eE2jjEGbbFc=",
    "PublicKey":  "3Ruirgw9qNRwNpBepkiVjjSe82tY+lDZr6WaFC4wO2g=",
    "PresharedKey": "GMMLKWdJlgsKVoR26BJPsNbDXyfILL+x1Nd6Ecmn4lg=",
    "PreUp":  "",
    "PreDown": "iptables -D FORWARD -i wg0 -j ACCEPT; iptables -D FORWARD -o wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o enp0s1 -j MASQUERADE;",
    "PostUp":  "iptables -A FORWARD -i wg0 -j ACCEPT; iptables -A FORWARD -o wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o enp0s1 -j MASQUERADE;",
    "PostDown": ""
}
```

| Parameter           | Type   |
|---------------------|--------|
| `ConfigurationName` | string |
| `Address`           | string |
| `ListenPort`        | int    |
| `PrivateKey`        | string |
| `PublicKey`         | string |
| `PresharedKey`      | string |
| `PreUp`             | string |
| `PreDown`           | string |
| `PostUp`            | string |
| `PostDown`          | string |

## Response

`200 - OK`

If everything is good

```json
{
    "data": null,
    "message": null,
    "status": true
}
```

If the new configuration's `ConfigurationName` is already existed

```json
{
    "data": null,
    "message": "Already have a configuration with the name \"wg0\"",
    "status": false
}
```

If the new configuration's `ListenPort` is used by another configuration

```json
{
    "data": null,
    "message": "Already have a configuration with the port  \"51820\"",
    "status": false
}
```

If the new configuration's `Address` is used by another configuration

```json
{
    "data": null,
    "message": "Already have a configuration with the address \"10.0.0.1/24\"",
    "status": false
}
```