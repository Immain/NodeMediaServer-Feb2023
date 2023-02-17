# NodeMediaServer-Feb2023
Media Server to push stream content or live video feeds to a media player on a hosted website

# Assign an SSL Cert to the Node Media Server
```
sudo snap install --classic certbot
```
```
sudo ln -s /snap/bin/certbot /usr/bin/certbot
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
