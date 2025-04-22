# Email Service

Starting v4.2.0, you'll be able to share your peers with email. To enable it, simply head to **Settings > WGDashboard Settings**:

> Currently, WGDashboard only support SMTP and SMTP w/ TLS. Please make sure your email provider supports logging in with SMTP. With my own experiments, **free tier** of Outlook(Hotmail) and Gmail disabled SMTP since last year, and no longer can enable it.

1. Scroll down to the **Email Account** section
2. Fill in the following fields
   1. Server
   2. Port
   3. Encryption
   4. Username (Your email address)
   5. Password
   6. Send From
3. Once everything is filled, you should see a green **Ready** top right of the form
4. Try to send a test email and see if everything works.
5. If yes, you can start editing the **Email Body Template**! Please read the following paragraph for more information.

**Email Body Template**

The template utilize the Jinja template engine to generate an HTML body for your email. In your template, there are **2** variables you can use:
- `peer` 
  - For example
   ```json
   {
      "DNS": "",
      "ShareLink": [],
      "allowed_ip": "10.0.0.3/32, 2001:db8:64:49::3/128",
      "configuration": {
         "Address": "10.0.0.1/28, 2001:db8:64:49::1/64",
         "ConnectedPeers": 0,
         "DataUsage": {
            "Receive": 0,
            "Sent": 0,
            "Total": 0
         },
         "ListenPort": "51823",
         "Name": "wg-external",
         "PostDown": "",
         "PostUp": "",
         "PreDown": "",
         "PreUp": "",
         "PrivateKey": "aC98hORPAbbxXZmy8qy1JP9Ip3JtEhbjDTOGtgHvmmg=",
         "Protocol": "wg",
         "PublicKey": "upH8PMbMzpcynJXz09Vldye09vzAmmNRV40hR+Vhbyw=",
         "SaveConfig": true,
         "Status": true,
         "TotalPeers": 13
      },
      "cumu_data": 0,
      "cumu_receive": 0,
      "cumu_sent": 0,
      "endpoint": "(none)",
      "endpoint_allowed_ip": "0.0.0.0/0",
      "id": "Wu/0xCr+n/caqDVKtjG+C9UelAvY/beARX3cW1i7LUI=",
      "jobs": [],
      "keepalive": 21,
      "latest_handshake": "No Handshake",
      "mtu": 1420,
      "name": "",
      "preshared_key": "",
      "private_key": "ABgsivKkBd6K9LizqHm/pDjfq2HRNESjdJBIz4RMlkE=",
      "remote_endpoint": "wg.local",
      "status": "stopped",
      "total_data": 0,
      "total_receive": 0,
      "total_sent": 0
   }
   ```
- `configurationFile`
  - For example
  ```json
  { 
    "fileName": "UntitledPeer", 
    "file": "[Interface]\\nPrivateKey = ABgsivKkBd6K9LizqHm/pDjfq2HRNESjdJBIz4RMlkE=\\nAddress = 10.0.0.3/32, 2001:db8:64:49::3/128\\nMTU = 1420\\n\\n[Peer]\\nPublicKey = upH8PMbMzpcynJXz09Vldye09vzAmmNRV40hR+Vhbyw=\\nAllowedIPs = 0.0.0.0/0\\nEndpoint = vpn.example.com:51823\\nPersistentKeepalive = 21\\n"
  } 
  ```
  
So if I have the following template

```
Hi,

Your WireGuard configuration is ready with the name "{{ peer.name }}", and its allowed IP address is: {{ peer.allowed_ip }}.

Please see the attached configuration file "{{ configurationFile.fileName }}" and open it on your iPhone with the WireGuard app. If you can't, please copy the following lines into a raw .conf file and send it to your phone:

------- Configuration start below this line -------

{{ configurationFile.file }}

------- Configuration end below this line -------

Best,
Donald Zou
```

The result will be like this:

```
Hi,

Your WireGuard configuration is ready with the name "", and its allowed IP address is: 10.0.0.3/32, 2001:db8:64:49::3/128.

Please see the attached configuration file "UntitledPeer" and open it on your iPhone with the WireGuard app. If you can't, please copy the following lines into a raw .conf file and send it to your phone:

------- Configuration start below this line -------

[Interface]
PrivateKey = ABgsivKkBd6K9LizqHm/pDjfq2HRNESjdJBIz4RMlkE=
Address = 10.0.0.3/32, 2001:db8:64:49::3/128
MTU = 1420

[Peer]
PublicKey = upH8PMbMzpcynJXz09Vldye09vzAmmNRV40hR+Vhbyw=
AllowedIPs = 0.0.0.0/0
Endpoint = vpn.example.com:51823
PersistentKeepalive = 21


------- Configuration end below this line -------

Best,
Donald Zou
```

Please be aware that it might reveal sensitive information like your configuration, please check before it got sent out.