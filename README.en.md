# bilibili embed image overlay

A tool to add more visual cue when embedding bilibili videos in GitHub.

## Run app localy

- Make sure to have [nix package manager](https://nixos.org/download.html) installed.
- Clone repo & cd into it.
- Run: `nix-shell`
- Inside the shell run `gunicorn -w 4 -b 0.0.0.0:8080 wsgi:app` and visit http://localhost:8080/

## Example

## Deployment & Hosting

### systemd service

```bash
cat <<'EOF' > /lib/systemd/system/bb-embed.service
[Unit]
Description=bb-embed

[Service]
Type=simple
Restart=always
RestartSec=5s
WorkingDirectory=/home/ubuntu/gh/bb-embed
ExecStart=/home/ubuntu/.nix-profile/bin/nix-shell -I /home/ubuntu/.nix-defexpr/channels --run "gunicorn -w 4 -b 0.0.0.0:9070 wsgi:app"

[Install]
WantedBy=multi-user.target
EOF

# must run start in /home/ubuntu/gh/bb-embed
cd /home/ubuntu/gh/bb-embed
sudo service bb-embed restart
```

### nginx config

```bash
cat <<'EOF' > /etc/nginx/sites-enabled/bb-embed-zjffun-com
server {
    server_name bb-embed.zjffun.com;
    listen 80;

    location / {
        proxy_pass http://localhost:9070;
    }
}
EOF
```

### HTTPS

```bash
sudo apt update
sudo apt -y install snapd
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx
```
