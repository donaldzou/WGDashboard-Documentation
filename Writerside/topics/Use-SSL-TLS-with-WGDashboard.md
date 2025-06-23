# Use SSL/TLS with WGDashboard

After through testing, I've decided not to use enable SSL/TLS on Gunicorn as it is not stable, it will stuck and load forever. 
But if you have any suggestions on how to make it work on Gunicorn, please let me know!

The solution we decided is to use **Nginx with Reverse Proxy**, and we discovered that let Nginx handle SSL/TLS is most stable.

## Requirement
- Nginx
- SSL/TLS Certificate

> Assuming your WGDashboard is running under port `10086` (default port)

### Step 1 - Run WGDashboard

```bash
$ ./wgd.sh start
=================================================================================
+          <WGDashboard> by Donald Zou - https://github.com/donaldzou           +
=================================================================================
[WGDashboard] ✅ WireGuard is already installed.
[WGDashboard] Starting WGDashboard with Gunicorn in the background.
[WGDashboard] Initialized Configuration: wg1
[Gunicorn] WGDashboard w/ Gunicorn will be running on 0.0.0.0:10086
[Gunicorn] Access log file is at ./log/access_2025_04_23_21_55_34.log
[Gunicorn] Error log file is at ./log/error_2025_04_23_21_55_34.log
[WGDashboard] Checking if WGDashboard w/ Gunicorn started successfully
[WGDashboard] WGDashboard w/ Gunicorn started successfully
---------------------------------------------------------------------------------
```
This would start WGDashboard in the background with Gunicorn.

### Step 2 - Configure Nginx

We'll need to create a config file for our Nginx site.

```bash
$ sudo nano /etc/nginx/sites-available/wgdashboard
```

Paste the following example into the file, and replace `[your_domain]` with your actual domain.

```
server {
    server_name [your_domain];
    listen 80;
    
    location / {
        proxy_pass http://0.0.0.0:10086;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
Then save and close the file.

Enable your site on Nginx
```bash
$ sudo ln -s /etc/nginx/sites-available/wgdashboard /etc/nginx/sites-enabled
$ sudo nginx -t
```
If you don't see any errors coming out, we can now restart Nginx to read your configuration.

```bash
$ sudo systemctl restart nginx
```

Try to access `http://[your_domain]` with your browser and see if you can reach WGDashboard. 
If yes then proceed to the next step to configure SSL/TLS.

### Step 3 - Configure SSL/TLS

#### If you already obtained Certificate and Private Key file

For users who already obtain their certificate, if you have the certificate file and private key, you can paste them into the Nginx config file

`/etc/nginx/sites-available/wgdashboard`
```
server {
    server_name [your_domain];
    listen 443 ssl;
    ssl_certificate [absolute path to your certificate]
    ssl_certificate_key [absolute path to your private key]
    
    location / {
        proxy_pass http://0.0.0.0:10086;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
server {
    server_name [your_domain];
    listen 80;
    
     if ($host = [your_domain]) {
        return 301 https://$host$request_uri;
    }
}
```

Save and close the file, restart Nginx and now try to access `https://[your_domain]`

#### If you haven't obtain Certificate and Private Key file

I would recommend to use **Certbot** to obtain a certificate. You can follow this [link](https://certbot.eff.org/instructions?ws=nginx&os=pip) on how to configure.

After configuring with Certbot, your Nginx site config file should looks like this:

```
server {
    server_name yourdomain.com;
    
    location / {
        proxy_pass http://0.0.0.0:10086;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
server {
    if ($host = yourdomain.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    server_name yourdomain.com;
    listen 80;
    return 404; # managed by Certbot
}
```