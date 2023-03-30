# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`


## Reverse-Proxy

After u have installed Nginx, Docker and have successfully run it as Container. Then we need to configure reverse_proxy as we want to give access to the application by using the concept of reverse-proxy.

For this we need to change the configuration of Nginx so for that go to /etc/nginx/sites-enabled location in your AWS EC2- Ubuntu Instance where all this setup was done

Then, we will update the default file for changing the configuration :

![Screenshot (3)](https://user-images.githubusercontent.com/98457309/228765979-c33c0254-3c01-43a4-81e0-b23b3032861c.png)

Here, we have added a proxy address for the incoming traffic.

After adding this, you need to restart the nginx so that updates will work.  
```
sudo systemctl restart nginx      #command to restart nginx
```

Now, you can access the application using the IP address.

Now the app is accessible, but we are not able to update or delete the notes here because the backend code is not updated to store such data.

For this, we need to copy all static files of the application to the location Nginx root folder /var/www/html so that we can access it.
```
sudo cp -r mynotes/build/* /var/www/html/
```

Now, we need to update the location /api for the backend page of the server.

Go to /etc/nginx/sites-enabled location and update the default code.

![Screenshot (4)](https://user-images.githubusercontent.com/98457309/228768143-9d3a3e38-2d91-471a-ae8a-5950812022a0.png)

Save it and Restart the nginx service.

After restarting, you can go on the browser and check accessing the notesapp and try updating it.

In this way, we did deploy our web application using the Nginx server.



