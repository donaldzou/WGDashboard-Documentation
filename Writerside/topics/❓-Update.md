# ❓ Update

> **Notice to users who are using `v3 - v3.0.6` and want to update to `v4.0`**
{style="warning"}

Although theoretically updating through `wgd.sh` should work, but I still suggest you to update the dashboard manually.

> **Notice to users who are using `v2.3.1` or below**
{style="warning"}

For user who is using `v2.3.1` or below, please notice that all data that stored in the current database will **not** transfer to the new database. This is hard decision to move from TinyDB to SQLite. But SQLite does provide a thread-safe access and TinyDB doesn't. I couldn't find a safe way to transfer the data, so you need to do them manually... Sorry about that :pensive:。 But I guess this would be a great start for future development :sunglasses:.

## How to update

1. Change your directory to `wgdashboard`

    ```shell
    cd wgdashboard/src
    ```

2. Update the dashboard
    ```shell
    git pull https://github.com/donaldzou/WGDashboard.git --force
    ```

3. Install

   ```shell
   sudo ./wgd.sh install
   ```

Starting with `v3.0`, you can simply do `sudo ./wgd.sh update` !! (I hope)