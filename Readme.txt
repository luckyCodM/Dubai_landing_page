============================================================
PROJECT README
============================================================

Project Name:
Malaysia Landing Page – CODM Software

Project URL:
https://malaysia.codmsoftware.com

Company:
CODM Software

Repository Purpose:
This repository contains the complete source code and deployment
instructions for the Malaysia regional landing page of CODM Software.

============================================================
PROJECT DESCRIPTION
============================================================

The Malaysia Landing Page is a static, responsive website created for
CODM Software to represent its services in the Malaysia region.

The website is built using a modern HTML template and deployed on a
Linux VPS server using the Nginx web server with SSL enabled.

The project is optimized for:
- Fast loading performance
- Mobile, tablet, and desktop devices
- SEO-friendly structure
- Easy maintenance and future updates

============================================================
TEMPLATE INFORMATION
============================================================

Template Name:
Dewi

Template Provider:
BootstrapMade

Template URL:
https://bootstrapmade.com/dewi-free-multi-purpose-html-template/

License:
https://bootstrapmade.com/license/

Note:
This project follows the licensing terms provided by BootstrapMade.
Commercial usage is allowed as per the license.

============================================================
TECHNOLOGY STACK
============================================================

Frontend:
- HTML5
- CSS3
- JavaScript
- Bootstrap Framework

Backend / Server:
- Ubuntu Linux VPS
- Nginx Web Server
- SSL via Certbot (Let’s Encrypt)

Version Control:
- Git
- GitHub Repository

============================================================
PROJECT FOLDER STRUCTURE
============================================================

malaysia.codmsoftware.com/
│
├── assets/
│   ├── css/        (Stylesheets)
│   ├── js/         (JavaScript files)
│   ├── img/        (Images)
│   └── vendor/     (Third-party libraries)
│
├── index.html      (Main website file)
├── README.txt      (Project documentation)
└── favicon.ico     (Website icon)

============================================================
STEP-BY-STEP DEPLOYMENT GUIDE
============================================================

STEP 1: SUBDOMAIN SETUP (DNS)

Create a subdomain in your domain DNS provider.

Type: A
Host: malaysia
Points To: 
TTL: Default

Result:
malaysia.codmsoftware.com points to your VPS server.

------------------------------------------------------------

STEP 2: CREATE PROJECT DIRECTORY ON SERVER

Login to your VPS via SSH and run:

mkdir -p /var/www/malaysia.codmsoftware.com
cd /var/www/malaysia.codmsoftware.com

------------------------------------------------------------

STEP 3: UPLOAD PROJECT FILES

Upload all project files to the directory using Git, SCP, or FTP.

Example using Git:

git clone YOUR_GITHUB_REPOSITORY_URL .

------------------------------------------------------------

STEP 4: SET FILE PERMISSIONS (IMPORTANT)

Correct permissions are required to avoid 403 Forbidden errors.

chown -R www-data:www-data /var/www/malaysia.codmsoftware.com
chmod -R 755 /var/www/malaysia.codmsoftware.com

------------------------------------------------------------

STEP 5: CREATE NGINX CONFIGURATION

Create a new Nginx config file:

sudo nano /etc/nginx/sites-available/malaysia.codmsoftware.com

Paste the following configuration:

server {
    listen 80;
    server_name malaysia.codmsoftware.com;

    root /var/www/malaysia.codmsoftware.com;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

------------------------------------------------------------

STEP 6: ENABLE NGINX SITE

Enable the configuration and reload Nginx:

ln -s /etc/nginx/sites-available/malaysia.codmsoftware.com /etc/nginx/sites-enabled/
nginx -t
systemctl reload nginx

------------------------------------------------------------

STEP 7: INSTALL SSL (HTTPS)

Secure the website using SSL:

sudo certbot --nginx -d malaysia.codmsoftware.com

After successful installation, the site will be accessible via HTTPS.

============================================================
SECURITY FEATURES
============================================================

- HTTPS enabled with SSL certificate
- Secure Nginx configuration
- Proper file ownership and permissions
- Optimized server setup

============================================================
CUSTOMIZATION GUIDE
============================================================

To update website content:
- Edit index.html for text and layout changes
- Replace images inside assets/img/
- Update CSS files inside assets/css/
- Update JavaScript inside assets/js/

============================================================
SEO & PERFORMANCE
============================================================

- Clean HTML structure
- Responsive mobile-first design
- Optimized assets
- Fast server response using Nginx

============================================================
MAINTENANCE & UPDATES
============================================================

- Use Git for version control
- Pull latest changes from GitHub when updating
- Reload Nginx after server configuration changes
- Renew SSL automatically via Certbot

============================================================
SUPPORT
============================================================

For maintenance, updates, or support:
CODM Software – Web Development Team

============================================================
PROJECT STATUS
============================================================

✔ Subdomain Configured
✔ Website Deployed
✔ Nginx Configured
✔ SSL Enabled
✔ Production Ready

============================================================
END OF FILE
============================================================
