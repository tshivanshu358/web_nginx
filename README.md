# web_nginx
Setup a Static Website Using Nginx

#Step 1: Update and Upgrade Your System
sudo apt update
sudo apt upgrade

#Step 2: Install Nginx
sudo apt install nginx
sudo systemctl start nginx
sudo systemctl enable nginx

#Step 3: Create Your Static Website
sudo mkdir -p /var/www/my_static_site        //command to create a new directory for your website
sudo nano /var/www/my_static_site/index.html //Create an HTML File

#Add Content to index.html 

#Step 4: Configure Nginx
Create a New Nginx Configuration File: 
sudo nano /etc/nginx/sites-available/my_static_site
Add Configuration to the File
server {
    listen 80;
    server_name localhost;

    root /var/www/my_static_site;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

Enable the New Site:
sudo ln -s /etc/nginx/sites-available/my_static_site /etc/nginx/sites-enabled/         //command to create a symbolic link to the sites-enabled directory

Test Nginx Configuration:
sudo nginx -t

Restart Nginx:
sudo systemctl restart nginx


 Access Your Static Website
 In the address bar, type http://localhost and press Enter.
