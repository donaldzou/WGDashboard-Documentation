# 📝 Requirements

1. Supported operating systems. Please view the list below.
2. WireGuard & WireGuard-Tools (`wg-quick`)
3. Python 3.10 / 3.11 / 3.12
4. `git`, `net-tools`, `sudo` (_This should only apply to RHEL 9 & 8, interestingly it doesn't have it preinstalled)_

## Supported Operating Systems

<note>
	All operating systems below are tested by myself. All are <b>ARM64</b> ran in UTM Virtual Machine.
</note>
<note>
	For Proxmox VE, please visit <a href="https://community-scripts.github.io/ProxmoxVE/scripts?id=wireguard">community script</a> to install

</note>

<tabs>
    <tab title="Ubuntu">
        <list type="bullet">
			<li>20.04 LTS</li>
			<li>22.04 LTS</li>
			<li>24.02 LTS</li>
		</list>
    </tab>
    <tab title="Debian">
        <list type="bullet">
			<li>12.6</li>
			<li>11.10</li>
		</list>
    </tab>
    <tab title="Red Hat Enterprise Linux">
        <list type="bullet">
			<li>9.4</li>
		</list>
    </tab>
    <tab title="CentOS">
        <list type="bullet">
			<li>9-Stream</li>
		</list>
    </tab>
	<tab title="AlmaLinux">
        <list type="bullet">
			<li>9.4 (Seafoam Ocelot)</li>
		</list>
    </tab>
    <tab title="Fedora">
        <list type="bullet">
			<li>40</li>
			<li>39</li>
			<li>38</li>
		</list>
    </tab>
    <tab title="Alpine Linux">
        <list type="bullet">
			<li>3.20.2</li>
		</list>
    </tab>
	<tab title="Rocky Linux">
        <list type="bullet">
			<li>9.4</li>
		</list>
    </tab>
	<tab title="Raspberry Pi OS">
		<list type="bullet">
			<li>Kernel Version: 6.6 w/ Debian 12 (Bookworm)</li>
		</list>
	</tab>
</tabs>

> If you installed WGDashboard on other systems without any issues, please let me know. Thank you!

## Existing WireGuard Configurations

<note>
This only applies to existing WireGuard Configuration under `/etc/wireguard`
</note>


```ini
[Interface]
...
SaveConfig = true
...

[Peer]
#Name# = Donald's iPhone
PublicKey = abcd1234
AllowedIPs = 1.2.3.4/32
```

> With `v4`, WGDashboard will look for entry with `#Name# = abc...` in each peer and use that for the name.