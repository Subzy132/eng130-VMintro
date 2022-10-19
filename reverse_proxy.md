# How to set up reverse proxy for an application

1. After having everything set up such as: nginx, nodejs and the normal website working we can start to work on making the reverse proxy
2. In the VM run `sudo nano /etc/nginx/sites-available/default`
3. You should get prompt showing the file content
4. scroll until you find location `location /`
5. replace everything in those curly brackets with 
   ```bash
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
   ```
6. change the port number to 3000
7. save the file
8. run `sudo nginx -t` to check if the syntax is correct
9. run `sudo systemctl restart nginx` to restart the nginx
10. `cd` your way back into the app folder and run
   1. `npm install`
   2. `npm start`
11. after getting the prompt that the app is running you can now visit the website without the 3000