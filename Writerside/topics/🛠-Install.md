# 🛠 Install

## Install Commands

These commands are tested by myself in each OS. It contains commands to install WireGuard, Git, Net Tools, and even Python on some OS.

<warning>
Please make sure you understand these commands before you run them.
</warning>

<tabs>
    <tab title="Ubuntu">
		<chapter title="20.04 LTS">
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
		<chapter title="22.04 LTS and 24.02 LTS">
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
    <tab title="Fedora">
		<chapter title="40, 39 and 38">
			<code-block lang="shell">
				sudo yum install wireguard-tools net-tools git -y && \
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
    <tab title="Alpine Linux">
		<chapter title="3.20.2">
			<code-block lang="shell">
				sudo yum install wireguard-tools net-tools git -y && \
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
</tabs>

## Manual Installation

> To ensure a smooth installation process, please make sure you have the following installed:
> - Python 3.10 or above
> - `git`
> - `wireguard-tools`
> - `net-tools`

1. Download WGDashboard

   ```shell
   git clone https://github.com/donaldzou/WGDashboard.git wgdashboard

2. Open the WGDashboard folder

   ```shell
   cd wgdashboard/src
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


