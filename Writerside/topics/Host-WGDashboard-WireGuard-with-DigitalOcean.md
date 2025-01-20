# Host WGDashboard &amp; WireGuard with DigitalOcean

## Step 1: Register

If you don't have a DigitalOcean account yet, you can click my referral button below and register with **DigitalOcean**, you will receive a **$200** credit for **60-days** to your server, and you can support this project too!

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%203.svg)](https://www.digitalocean.com/?refcode=a84cb9aac585&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

> When you choose to use the link above, and spent **\$25** after your credits, I will receive **$25 in credits** towards my servers on this project :) **Thanks in advance!**

## Step 2: Create a WGDashboard Droplet

<video src="https://www.youtube.com/watch?v=VnTnLBq2cOI"/>


1. After the registration process, head to [WGDashboard | DigitalOcean Marketplace](https://marketplace.digitalocean.com/apps/wgdashboard)
2. Click the **blue** button with **Create WGDashboard Droplet** on the right side
3. Once the page loaded, you can choose a region that is closest to you or the one you preferred
4. Keep the image chosen as **WGDashboard latest on Ubuntu**
5. Then scroll down to choose **Regular** CPU option, and pick the **$6** one as it is already good enough to host WGDashboard and WireGuard
6. Scroll down to either create a **root** password or upload your SSH Key
7. Scroll down to the bottom to change the **Hostname** of your server
8. Once everything is done, click **Create Droplet**
9. You will see the progress bar of your droplet, once it is done, you can see its **IP address**.
10. You should also see a **Get started** button right next to the **IP address**, let's click that
11. Then follow the instructions on the popup :)
	- You should see the instruction similar to this: 
      1. `ssh root@...`
      2. Enter sudo `systemctl status wg-dashboard.service` to check the status
      3. If you see the service is Active, use your browser to visit `http://....:10086`
12. Once you finished following the instruction, click the big **Quick access to WGDashboard** and enjoy!