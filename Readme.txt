============================================================
PROJECT README
============================================================

Project Name:
Dubai Landing Page – CODM Software

Project URL:
https://dubai.codmsoftware.com

Company:
CODM Software

Repository Type:
Static Landing Page Website

============================================================
PROJECT OVERVIEW
============================================================

This repository contains the complete source code for the
Dubai Landing Page website developed for CODM Software.

The project is a static website built using HTML, CSS, and
JavaScript and is designed to be fast, responsive, and
SEO-friendly. It is deployed on a Linux VPS using the
Nginx web server with SSL enabled.

============================================================
FEATURES
============================================================

- Fully responsive design (mobile, tablet, desktop)
- Clean and modern UI
- Fast loading static website
- SEO-friendly HTML structure
- Easy to deploy and maintain
- Secure hosting with HTTPS

============================================================
TECHNOLOGY STACK
============================================================

Frontend:
- HTML5
- CSS3
- JavaScript
- Bootstrap Framework

Server & Deployment:
- Ubuntu Linux VPS
- Nginx Web Server
- SSL via Let’s Encrypt (Certbot)

Version Control:
- Git
- GitHub

============================================================
PROJECT FOLDER STRUCTURE
============================================================

Dubai_landing_page/
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

NOTE:
Only index.html and assets/ are required on the production server.

============================================================
STEP-BY-STEP DEPLOYMENT GUIDE
============================================================

------------------------------------------------------------
STEP 1: CREATE SUBDOMAIN (DNS)
------------------------------------------------------------

Create a subdomain in your DNS provider.

Type: A
Host: dubai
Points To: YOUR_VPS_IP
TTL: Default

Result:
dubai.codmsoftware.com → VPS IP

------------------------------------------------------------
STEP 2: CONNECT TO VPS
------------------------------------------------------------

Login to your server:

ssh root@YOUR_VPS_IP

------------------------------------------------------------
STEP 3: CREATE WEB DIRECTORY
------------------------------------------------------------

mkdir -p /var/www/dubai.codmsoftware.com
cd /var/www/dubai.codmsoftware.com

------------------------------------------------------------
STEP 4: UPLOAD PROJECT FILES
------------------------------------------------------------

Upload the project files using Git, SCP, or FTP.

Example using Git:

git clone YOUR_GITHUB_REPOSITORY_URL .

------------------------------------------------------------
STEP 5: REMOVE UNNECESSARY FILES (PRODUCTION)
------------------------------------------------------------

rm -rf .git
rm -f .DS_Store

------------------------------------------------------------
STEP 6: SET FILE PERMISSIONS (IMPORTANT)
------------------------------------------------------------

chown -R www-data:www-data /var/www/dubai.codmsoftware.com
chmod -R 755 /var/www/dubai.codmsoftware.com

------------------------------------------------------------
STEP 7: CREATE NGINX CONFIGURATION
------------------------------------------------------------

nano /etc/nginx/sites-available/dubai.codmsoftware.com

Paste:

server {
    listen 80;
    server_name dubai.codmsoftware.com;

    root /var/www/dubai.codmsoftware.com;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

------------------------------------------------------------
STEP 8: ENABLE NGINX SITE
------------------------------------------------------------

ln -s /etc/nginx/sites-available/dubai.codmsoftware.com /etc/nginx/sites-enabled/
nginx -t
systemctl reload nginx

------------------------------------------------------------
STEP 9: ENABLE SSL (HTTPS)
------------------------------------------------------------

certbot --nginx -d dubai.codmsoftware.com

============================================================
COMMON ISSUES & FIXES
============================================================

403 Forbidden Error:
- Fix file ownership and permissions
- Ensure index.html exists in root directory

404 Not Found:
- Check Nginx root path
- Ensure files are not inside nested folders

Images Not Loading:
- Use absolute paths (/assets/img/)
- Check file name case sensitivity

============================================================
CUSTOMIZATION GUIDE
============================================================

- Edit index.html to update content
- Replace images inside assets/img/
- Modify styles in assets/css/
- Update scripts in assets/js/

============================================================
SECURITY BEST PRACTICES
============================================================

- Remove .git folder from production server
- Use proper file permissions
- Enable HTTPS
- Keep server packages updated

============================================================
MAINTENANCE
============================================================

- Use GitHub for version control
- Deploy updates manually or via CI/CD
- Reload Nginx after configuration changes
- SSL renews automatically

============================================================
PROJECT STATUS
============================================================

✔ Project Uploaded
✔ Server Configured
✔ Nginx Enabled
✔ SSL Enabled
✔ Production Ready

============================================================
SUPPORT
============================================================

For support or maintenance:
CODM Software – Web Development Team

============================================================
END OF FILE
============================================================
