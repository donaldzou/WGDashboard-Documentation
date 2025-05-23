# 🛠 Install

> **For AmneziaWG Users**
> 
> Starting from v4.2.0, WGDashboard support AmneziaWG, but since it has completely installation method than WireGuard, we decided **not to include** in our installation described below, you'll need to follow the AmneziaWG official documentation to install: [Link](https://github.com/amnezia-vpn/amneziawg-linux-kernel-module)

There are 4 options to install WGDashboard

## Option 1: Host WGDashboard & WireGuard with DigitalOcean

WGDashboard is now available as a **1-Click** app on DigitalOcean! **[Follow this instruction to host](Host-WGDashboard-WireGuard-with-DigitalOcean.md)**

## Option 2: Install WGDashboard with a command

These commands are tested by myself in each operating system listed below. It contains commands to install WireGuard, Git, Net Tools, and even Python on some OS.

| Operating System                | Version(s)                                   |
|---------------------------------|----------------------------------------------|
| Ubuntu                          | 20.04 (LTS), 22.04 (LTS), 24.04 (LTS), 24.10 |
| Debian                          | 12.6, 11.10                                  |
| Red Hat Enterprise Linux (RHEL) | 9.4                                          |
| CentOS                          | 9-Stream                                     |
| AlmaLinux                       | 9.4 (Seafoam Ocelot)                         |
| Fedora                          | 38, 39, 40, 41                               |
| Alpine Linux                    | 3.20.2                                       |
| Rocky Linux                     | 9.4                                          |
| Raspberry Pi OS                 | Kernel Version: 6.6 w/ Debian 12 (Bookworm)  |


<warning>
Please make sure you understand these commands before you run them.
</warning>

<tabs>
   <tab title="Ubuntu">
      <chapter title="20.04 (LTS)">
         <code-block lang="shell">
             sudo add-apt-repository ppa:deadsnakes/ppa -y && \
             sudo apt-get update -y && \
             sudo apt-get install python3.10 python3.10-distutils wireguard-tools net-tools --no-install-recommends -y && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p
         </code-block>
      </chapter>
      <chapter title="22.04 (LTS), 24.04 (LTS) and 24.10">
         <code-block lang="shell">
             sudo apt-get update -y && \
             sudo apt install wireguard-tools net-tools --no-install-recommends -y && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf
         </code-block>
      </chapter>
   </tab>
   <tab title="Debian">
      <chapter title="12.6">
         <code-block lang="shell">
             apt-get install sudo git iptables -y && \ 
             sudo apt-get update && \
             sudo apt install wireguard-tools net-tools && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf
         </code-block>
      </chapter>
      <chapter title="11.10">
         <warning>This commands will download Python 3.10's source code and build from it, since Debian 11.10 doesn't come with Python 3.10</warning>
         <code-block lang="shell">
             apt-get install sudo -y && \ 
             sudo apt-get update && \ 
             sudo apt install -y git iptables build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev wget libbz2-dev wireguard-tools net-tools && \ 
             wget https://www.python.org/ftp/python/3.10.0/Python-3.10.0.tgz && \ 
             tar -xvf Python-3.10.0.tgz && \ 
             cd Python-3.10.0 && \ 
             sudo ./configure --enable-optimizations && \ 
             sudo make && \ 
             sudo make altinstall && \ 
             cd .. && \ 
             git clone https://github.com/donaldzou/WGDashboard.git && \ 
             cd ./WGDashboard/src && \ 
             chmod +x ./wgd.sh && \ 
             ./wgd.sh install && \ 
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf
         </code-block>
      </chapter>
   </tab>
   <tab title="Red Hat Enterprise Linux">
      <chapter title="9.4">
         <code-block lang="shell">
             sudo yum install wireguard-tools net-tools git python3.11 -y && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf && \
             firewall-cmd --add-port=10086/tcp --permanent && \
             firewall-cmd --add-port=51820/udp --permanent && \
             firewall-cmd --reload
         </code-block>
      </chapter>
   </tab>
   <tab title="CentOS">
      <chapter title="9-Stream">
         <code-block lang="shell">
             sudo yum install wireguard-tools net-tools git python3.11 -y && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf && \
             firewall-cmd --add-port=10086/tcp --permanent && \
             firewall-cmd --add-port=51820/udp --permanent && \
             firewall-cmd --reload
         </code-block>
      </chapter>
   </tab>
   <tab title="AlmaLinux">
        <chapter title="9.4 (Seafoam Ocelot)">
            <code-block lang="shell">
                sudo yum install wireguard-tools net-tools git python3.11 -y && \
                git clone https://github.com/donaldzou/WGDashboard.git && \
                cd ./WGDashboard/src && \
                chmod +x ./wgd.sh && \
                ./wgd.sh install && \
                sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
                sudo sysctl -p /etc/sysctl.conf && \
                firewall-cmd --add-port=10086/tcp --permanent && \
                firewall-cmd --add-port=51820/udp --permanent && \
                firewall-cmd --reload
            </code-block>
        </chapter>
   </tab>
   <tab title="Fedora">
      <chapter title="38, 39, 40, 41">
         <code-block lang="shell">
             sudo yum install wireguard-tools net-tools git -y && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf
         </code-block>
      </chapter>
   </tab>
   <tab title="Alpine Linux">
		<chapter title="3.20.2">
			<code-block lang="shell">
               setup-interfaces -a ; \
               rc-service networking --quiet start ; \
               apk update ; \
               apk add wireguard-tools python3 python3-dev git iptables net-tools gcc musl-dev linux-headers sudo ; \
               git clone https://github.com/donaldzou/WGDashboard.git ; \
               cd ./WGDashboard/src ; \
               chmod +x ./wgd.sh ; \
               ./wgd.sh install
			</code-block>
		</chapter>
    </tab>
   <tab title="Rocky Linux">
      <chapter title="9.4">
         <code-block lang="shell">
             sudo yum install wireguard-tools net-tools git python3.11 -y && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf && \
             firewall-cmd --add-port=10086/tcp --permanent && \
             firewall-cmd --add-port=51820/udp --permanent && \
             firewall-cmd --reload
         </code-block>
      </chapter>
   </tab>
   <tab title="Raspberry Pi OS">
      <chapter title="Kernel Version: 6.6 w/ Debian 12 (Bookworm)">
         <code-block lang="shell">
             apt-get install sudo git iptables -y && \ 
             sudo apt-get update && \
             sudo apt install wireguard-tools net-tools && \
             git clone https://github.com/donaldzou/WGDashboard.git && \
             cd ./WGDashboard/src && \
             chmod +x ./wgd.sh && \
             ./wgd.sh install && \
             sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf && \
             sudo sysctl -p /etc/sysctl.conf
         </code-block>
         <tip>Tested by our community member. Thank you!</tip>
      </chapter>
   </tab>
</tabs>

## Option 3: Install with Proxmox Virtual Environment

Please visit this [community script](https://community-scripts.github.io/ProxmoxVE/scripts?id=wireguard) to install.


## Option 4: Manually install WGDashboard

> To ensure a smooth installation process, please make sure you have the following installed:
> - Python 3.10 or above
> - `git`
> - `wireguard-tools`
> - `net-tools`

1. Download WGDashboard

   ```shell
   git clone https://github.com/donaldzou/WGDashboard.git

2. Open the WGDashboard folder

   ```shell
   cd WGDashboard/src
   ```

3. Install WGDashboard

   ```shell
   sudo chmod u+x wgd.sh && \
   sudo ./wgd.sh install
   ```

4. Give read and execute permission to root of the WireGuard configuration folder, you can change the path if your configuration files are not stored in `/etc/wireguard`

   ```shell
   sudo chmod -R 755 /etc/wireguard
   ```

5. Run WGDashboard

   ```shell
   sudo ./wgd.sh start
   ```

6. Access dashboard

   Access your server with port `10086` (e.g. http://your_server_ip:10086), using username `admin` and password `admin`. See below how to change port and ip that the dashboard is running with.

7. Allow traffic forwarding (Optional, but recommend for most users)
   ```shell
   sudo echo "net.ipv4.ip_forward=1" >> /etc/sysctl.conf
   sudo sysctl -p /etc/sysctl.conf
   ```

## Looking for server to configure WireGuard and WGDashboard?

Click my referral button below and register with **DigitalOcean**, you will receive a **$200** credit for **60-days** to your server, and you can support this project too!

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%203.svg)](https://www.digitalocean.com/?refcode=a84cb9aac585&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)
#### How to support?
When you choose to use the link above, and spent **\$25** after your credits, I will receive **$25 in credits** towards my servers on this project :) **Thanks in advance!**
