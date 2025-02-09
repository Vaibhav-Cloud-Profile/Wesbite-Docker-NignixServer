# Wesbite-Docker-NignixServer
In this I have Deployed My Website into Docker Conatiner and hosted on Nignx Server.



Steps to follow


1)First Install Docker on Your Computer and see its Version docker --version and also installed Docker Desktop App and keep it always open when working with Docker.
2) create or open your website directory in VS Code and Create nginx.conf file and Dockerfile

   ngnix.conf file : 
   
   server {
    listen 80;
    server_name localhost;

    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page 404 /404.html;
}


  Dockerfile :
  

# Use the official Nginx image
FROM nginx:latest

# Copy custom Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy website files to Nginx HTML directory
COPY website /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]





3) Now build the docker image    docker build -t foldername-nginx .
4) now Run the Container docker run -d -p 8080:80 --name portfolio-container portfolio-nginx
5) Now Test your Website go to browser https://localhost:8080


Share Link with your Fiends:
in your VS Code terminal type ipconfig copy ipv4 address and sharre with your friend type https://ipv4 address:8080 make your friend is also on same wifi or internet.


Conclusion:  Your Webiste is live on Browser 
