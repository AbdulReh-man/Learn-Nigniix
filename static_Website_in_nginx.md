# 1) Create a Directory for your Site in /var/www/< Directory >

```bash
sudo mkdir -p /var/www/<Directory Name>
```

## By default there is an html Directory present

# 2) Copy Your Site to the Server Directory

### Copy them directly if you're working on the server

##### Copy an Entire Directory

```bash
cp -r /source/directory/path /destination/directory/path
```

#### Copy a Single File

```bash
cp /source/file/path /destination/file/path
```

# OR

### Command to upload from local to server

```bash
scp -r /path/to/my_site username@your_server_ip:/var/www/my_site
```

`/path/to/my_site:` The absolute path to the directory on your local machine.

`username:` The username you use to log in to the remote server.

`your_server_ip:` The IP address of your server.

`/var/www/my_site:` The path on the server where you want to copy the files.

# 2) Go to /etc/nginx/sites-enabled

#### Create a filename like "dahboard"

```bash
sudo touch dashboard
```

## Open file in Editor

#### For Nano Editor:

```bash
sudo nano < filename >
```

#### Example for Nano Editor

```bash
sudo nano dashboard
```

#### For Vim Editor:

```bash
sudo vim < filename >
```

#### Example for Vim Editor

```bash
sudo vim dashboard
```

# 3) Write some configuration code in this file

```bash
server {
    listen 80;
    server_name your_domain_or_IP;

    root /var/www/my_react_app;
    index index.html;

    location / {
        try_files $uri /index.html;
    }
}
```

`server_name` is a domain name

`root contain` the static file location

### Example

```bash
server {
listen 80;
server_name mydomain.me;

    root /var/www/dashboard;

    index index.html;

    location / {
        try_files $uri /index.html;
    }

}
```

# 3) Enable the Site in Nginx

Enable the configuration by creating a symbolic/Soft link:

```bash
sudo ln -s /etc/nginx/sites-available/my_react_app /etc/nginx/sites-enabled/
```

### Example

```bash
sudo ln -s /etc/nginx/sites-available/dashboard /etc/nginx/sites-enabled/
```

# 4) Check nginx service

### Test the Nginx configuration to ensure there are no syntax errors

```bash
sudo nginx -t
```

# 5) Reload Nginx

```bash
sudo systemctl restart nginx
```

### OR

```bash
sudo service nginx restart
```

# Now your site available for every one

### Access Your Website

```bash
http://your_server_ip
```

### Example

```bash
http://abdulrehmandev.me/
```
