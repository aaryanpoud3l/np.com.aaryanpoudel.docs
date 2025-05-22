---
title: "Symbolic Link / Symlink"
date: 2025-05-22T16:30:00+01:00
categories: ['Setups']
tags: ["cheatsheet,setup,linux"]
---

# Configuring a VPS

### Init:
1. Add your public key to VPS:
```sh
#In Local
pbcopy < ~/.ssh/id_ed25519.pub

#In VPS
nano ~/.ssh/authorized_keys  # Add .pub content here
```

2. Update & Upgrade:
   `sudo apt update && sudo apt upgrade`

3. Check if reboot required:
   `ls /var/run/reboot-required`

4. Change root pw:
```sh
sudo su
passwd
```

5. Create non-root user & add to sudoers group:
```sh
useradd userName
usermod -aG sudo userName
```

6. Add your public key (local) to newUser's authorized_keys file (in VPS) (Step 1)

7. SSH into the VPS as the created user
```sh
#Either Specify Input Key
ssh -i ~/.ssh/id_ed25519.pub userName@publicIP

#OR, manage with ssh config
nano ~/.ssh/config
#Config
Host serverName
  HostName publicIP
  Port 22
  User userName
  IdentityFile ~/.ssh/localPrivate.key
#And, login using serverName
ssh serverName 
```

8. Disable password login & root login: Inside these files, set `PasswordAuthentication no`
```sh
sudo nano /etc/ssh/sshd_config
#Add
PasswordAuthentication no
PermitRootLogin no

sudo nano /etc/ssh/sshd_config.d/someCloudImageSettings.conf
#Add
PasswordAuthentication no

sudo service ssh restart
```

9. Firewall Config:
```sh
sudo ufw status numbered
sudo ufw show listening

sudo ufw allow 22/tcp
sudo ufw allow 'Nginx Full'
sudo service ssh restart #OR try systemctl daemon-reload
```

10. Site Files & Permissions:
Point the subdomain from cloudflare to the serverIP using A record & Server IP *(DNS Only)*
```sh
sudo apt install nginx curl git -y
sudo mkdir -p /var/www/sub.domain.com/

#Change Permissions
sudo chown -R $USER:$USER /var/www/sub.domain.com
sudo chmod -R 755 /var/www/sub.domain.com
sudo echo 'hello world' > /var/www/sub.domain.com/index.html
```

11. Nginx Config:
```sh
sudo nano /etc/nginx/sites-available/sub.domain.com
#In the file above, paste config, change domain & root dir

server {
    listen 80;
    server_name sub.domain.com www.sub.domain.com;

    root /var/www/sub.domain.com/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

#Create Symlink
sudo ln -s /etc/nginx/sites-available/sub.domain.com /etc/nginx/sites-available/sub.domain.com
sudo nginx -t
sudo systemctl restart nginx

#Open Nginx ports on UFW
sudo ufw allow 'Nginx Full'
```
Also, open port from VPS provider dashboard > networking > subnet > security > vcn > security rules > Add Ingress Rules: Source CIDR `0.0.0.0/0` & Destination Port Range `80, 443`

Site should now be assessible via http using `curl http://sub.domain.com`

12. SSL Certificate using Let's Encrypt
```sh
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d sub.domain.com -d www.sub.domain.com

#For Autorenwal of ssl cert using cron, add the following line 
sudo crontab -e 
#add the following:
0 3 * * * /usr/bin/certbot renew --quiet
```

Site should now be assessible via https using `curl https://sub.domain.com` , From cloudflare, you can enable proxy