# NodeMediaServer-Feb2023
Media Server to push stream content or live video feeds to a media player on a hosted website. This script also installs NGINX Proxy Manager and Portainer Agent to easily access and manage the NGINX Proxy Manager container from any Portainer Instance. If the Node Media Server is hosted locally, you can use the installed NGINX proxy manager to assign the SSL Cert. If this is going to be hosted on a cloud service, then you have to use CertBot to manually install the cert and add it to your app.js file. 

# Script OS
Script was made for use on Ubuntu 20.04 and up

# Install Ansible (Ubuntu)
```
sudo apt install ansible && cd ansible
```
```
sudo nano launch.yml
```
Paste the contents and save.
```
sudo ansible-playbook launch.yml
```

# Assign an SSL Cert to the Node Media Server
```
sudo snap install --classic certbot
```
```
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
```
sudo ufw allow 80
```
```
sudo ufw allow 443
```
```
sudo ufw allow 8443
```
```
sudo certbot certonly --standalone -d your_domain
```
# Add the Certificate to your App.js File
```
  https: {
    port: 8443,
    key: '/etc/letsencrypt/live/your-domain/privkey.pem',
    cert: '/etc/letsencrypt/live/your-domain/fullchain.pem',
  },
```
# Launch Node Media Server
```
sudo node app.js
```
# Domain and Adding to a Web Based Media Player
Purchase a domain, or if you already own a domain, add a sub domain such as video.your-domain.com or vice versa. Set the Sub Domain as a CNAME or A record and assign it the Public IP address of your local or cloud machine. From there, use a compatible player on your side that uses either HLS or DASH and then set the source as:
```
https://video.your-domain.com:8443/live/stream/index.m3u8
```

