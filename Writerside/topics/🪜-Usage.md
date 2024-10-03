# 🪜 Usage

> The following commands are assumed you're in `wgdashboard/src`

## Start

This command will start WGDashboard and run it in the background.

```shell
./wgd.sh start
```

## Stop

This command will stop WGDashboard.

```shell
./wgd.sh stop
```

## Restart

This command will stop and start WGDashboard in the background.

```shell
./wgd.sh restart
```

## Debug Mode

This command will run WGDashboard in the foreground and output logs on the screen.

```shell
./wgd.sh debug
```

## Run WGDashboard as a system service

> This feature require WGDashboard v2.0 or above

In the `src` folder, it contained a file called `wg-dashboard.service`, we can use this file to let our system autostart the dashboard after reboot. The following guide has tested on **Ubuntu**, most **Debian** based OS might be the same, but some might not. Please don't hesitate to provide your system if you have tested the autostart on another system.

1. Changing the directory to the dashboard's directory

   ```shell
   cd wgdashboard/src
   ```

2. Get the full path of the dashboard's directory

   ```shell
   pwd
   #Output: /root/wgdashboard/src
   ```

   For this example, the output is `/root/wireguard-dashboard/src`, your path might be different since it depends on where you downloaded the dashboard in the first place. **Copy the the output to somewhere, we will need this in the next step.**

3. Edit the service file, the service file is located in `wireguard-dashboard/src`, you can use other editor you like, here will be using `nano`

   ```shell
   nano wg-dashboard.service
   ```

   You will see something like this:

   ```ini
   [Unit]
   After=syslog.target network-online.target
   Wants=wg-quick.target
   ConditionPathIsDirectory=/etc/wireguard
   
   [Service]
   Type=forking
   PIDFile=<absolute_path_of_wgdashboard_src>/gunicorn.pid
   WorkingDirectory=<absolute_path_of_wgdashboard_src>
   ExecStart=<absolute_path_of_wgdashboard_src>/wgd.sh start
   ExecStop=<absolute_path_of_wgdashboard_src>/wgd.sh stop
   ExecReload=<absolute_path_of_wgdashboard_src>/wgd.sh restart
   TimeoutSec=120
   PrivateTmp=yes
   Restart=always
   
   [Install]
   WantedBy=multi-user.target
   ```

   Now, we need to replace all `<absolute_path_of_wgdashboard_src>` to the one you just copied from step 2. After doing this, the file will become something like this, your file might be different:

   **Be aware that after the value of `WorkingDirectory`, it does not have  a `/` (slash).** And then save the file after you edited it

4. Copy the service file to systemd folder

   ```bash
   $ sudo cp wg-dashboard.service /etc/systemd/system/wg-dashboard.service
   ```

   To make sure you copy the file successfully, you can use this command `cat /etc/systemd/system/wg-dashboard.service` to see if it will output the file you just edited.

5. Enable the service

   ```bash
   $ sudo chmod 664 /etc/systemd/system/wg-dashboard.service
   $ sudo systemctl daemon-reload
   $ sudo systemctl enable wg-dashboard.service
   $ sudo systemctl start wg-dashboard.service  # <-- To start the service
   ```

6. Check if the service run correctly

   ```bash
   $ sudo systemctl status wg-dashboard.service
   ```
   And you should see something like this

   ```shell
    ● wg-dashboard.service
    Loaded: loaded (/etc/systemd/system/wg-dashboard.service; enabled; vendor preset: enabled)
    Active: active (running) since Wed 2024-08-14 22:21:47 EDT; 55s ago
    Process: 494968 ExecStart=/root/wgdashboard/src/wgd.sh start (code=exited, status=0/SUCCESS)
    Main PID: 495005 (gunicorn)
    Tasks: 5 (limit: 4523)
    Memory: 36.8M
    CPU: 789ms
    CGroup: /system.slice/wg-dashboard.service
    ├─495005 /root/wgdashboard/src/venv/bin/python3 ./venv/bin/gunicorn --config ./gunicorn.conf.py
    └─495007 /root/wgdashboard/src/venv/bin/python3 ./venv/bin/gunicorn --config ./gunicorn.conf.py
    
    Aug 14 22:21:40 wg sudo[494978]:     root : PWD=/root/wgdashboard/src ; USER=root ; COMMAND=./venv/bin/gunicorn --config ./gunicorn.conf.py
    Aug 14 22:21:40 wg sudo[494978]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=0)
    Aug 14 22:21:40 wg wgd.sh[494979]: [WGDashboard] WGDashboard w/ Gunicorn will be running on 0.0.0.0:10086
    Aug 14 22:21:40 wg wgd.sh[494979]: [WGDashboard] Access log file is at ./log/access_2024_08_14_22_21_40.log
    Aug 14 22:21:40 wg wgd.sh[494979]: [WGDashboard] Error log file is at ./log/error_2024_08_14_22_21_40.log
    Aug 14 22:21:40 wg sudo[494978]: pam_unix(sudo:session): session closed for user root
    Aug 14 22:21:45 wg wgd.sh[494968]: [WGDashboard] Checking if WGDashboard w/ Gunicorn started successfully
    Aug 14 22:21:47 wg wgd.sh[494968]: [WGDashboard] WGDashboard w/ Gunicorn started successfully
    Aug 14 22:21:47 wg wgd.sh[494968]: ------------------------------------------------------------
    Aug 14 22:21:47 wg systemd[1]: Started wg-dashboard.service.
   ```

   If you see `Active:` followed by `active (running) since...` then it means it run correctly.

7. Stop/Start/Restart the service

   ```bash
   sudo systemctl stop wg-dashboard.service      # <-- To stop the service
   sudo systemctl start wg-dashboard.service     # <-- To start the service
   sudo systemctl restart wg-dashboard.service   # <-- To restart the service
   ```

8. **And now you can reboot your system, and use the command at step 6 to see if it will auto start after the reboot, or just simply access the dashboard through your browser. If you have any questions or problem, please report it in the issue page.**

### Enable WireGuard configuration when WGDashboard start

> Thanks to the solution from [@opit7](https://github.com/donaldzou/WGDashboard/issues/360#issuecomment-2374004622)

You can add this in the service file. For example you want to enable `wg0` when WGDashboard start

```ini
...

[Service]
...
ExecStartPre=wg-quick up wg0

...
```

So now `wg0` will start before WGDashboard starts.