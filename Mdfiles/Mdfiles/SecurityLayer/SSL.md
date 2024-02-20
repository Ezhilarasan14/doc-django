# Security Layer

## SSL

To set up SSL with Nginx using Let's Encrypt on Ubuntu, you can follow these steps. Let's assume you have Nginx already installed and configured for your website. If not, install Nginx and set up your website before proceeding.


## Install Certbot:
```
sudo apt-get update
sudo apt-get install certbot python3-certbot-nginx
```

## Obtain SSL Certificate:

```
sudo certbot --nginx -d your_domain.com -d www.your_domain.com
```

## Certbot will handle the SSL configuration for Nginx automatically.

#### Test Nginx Configuration:

```
sudo nginx -t
```

#### Restart Nginx:

```
sudo systemctl restart nginx
```
#### Set up Automatic Renewal:

```
sudo crontab -e

Add the following line: markdown

0 */12 * * * certbot renew
```

https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04