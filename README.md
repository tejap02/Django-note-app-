# Django-note-app-
Nginx through routing Django project

# Requirements
1.Python 3.9
2.Node.js
3.React

# Installation
1.Clone the repository
git clone https://github.com/LondheShubham153/django-notes-app.git

2. sudo apt update

   sudo apt get insatll docker.io

   sudo usermod -aG docker $USER

   sudo reboot

   docker ps
# Build the app
    docker build -t notes-app .
# RUN the app
   docker run -d -p 8000:8000 notes-app:latest
   curl -L http://127.0.0.1:8000
   
# Nginx Installation
  Install Nginx reverse proxy to make this application available

  sudo apt-get update sudo apt install nginx

3.cd
  cd /etc/nginx/sites-enabled/
  ls
  sudo vim default
   server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html;
   
    server_name _;

    location / {
        proxy_pass http://127.0.0.1:8000;
        try_files $uri $uri/ =404;
    }
    location /api {
     proxy_pass http://127.0.0.1:8000/api;
        }
}

  sudo systemctl restart nginx
  
  cd django-notes-app/
  
  cd mynotes/
  
  cd build/
  
  sudo cp -r * /var/www/html/
  
