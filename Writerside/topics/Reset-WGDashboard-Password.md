# Reset WGDashboard Password

If you ever forgot your password WGDashboard, you can simply do the following:
1. `ssh` into your server
2. Navigate to WGDashboard's `src` directory
	```bash
	cd WGDashboard/src
	```
3. Shutdown WGDashboard
   - If you start WGDashboard with `./wgd.sh start`
   
       ```bash
       ./wgd.sh stop
       ```
   - If you start WGDashboard with service file

	   ```bash
	   sudo systemctl stop wg-dashboard
	   ```
4. Backup `wg-dashboard.ini`
	```Shell
	`cp ./wg-dashboard.ini ./wg-dashboard.ini.backup`
    ```
5. Use a text editor that you're familiar with, for example `nano` to edit `wg-dashboard.ini`
6. To reset password, remove the line starting with `password = ...` under the `[Account]` section, and **save** the file.
7. Restart WGDashboard and sign in with the default password:  `admin`
8. After signed in, head to **Settings > WGDashboard Settings > Account Settings** to update with your own password.

<note>
When editing <code>wg-dashboard.ini</code>, please be careful not to change/remove other settings. If you do please make sure you understand what you're doing, and create backups before any changes.
</note>