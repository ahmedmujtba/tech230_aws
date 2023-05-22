# AWS EC2 Automation (App & DB)

In this file we'll learn how to automate the ec2 instances for both the app and db.
You will need to have completed the following steps before we can start automation:

1. EC2 instance for app running.
2. EC2 instance for db running.

## Shell Script for Database

1. Create a shell script with `#!/bin/bash` at the start of the file.
2. Now include the following in your script:

- `sudo apt-get update -y` - to update relevant packages
- `sudo apt-get upgrade -y` - to upgrade relevant packages
- `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927` - To authenticate MongoDb
- `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20` - To install MongoDB
- `sudo sed -i "s+127.0.0.1+0.0.0.0+" /etc/mongod.conf` - To change the bindip so app can connect to the database.
- `sudo systemctl restart mongodb` - To restart MongoDB
- `sudo systemctl enable mongodb` - To enable MongoDB

## Shell Script for App

1. Create a shell script with `#!/bin/bash` at the start of the file.
2. Now add the following to your script:

- `sudo apt-get update -y` - to update relevant packages
- `sudo apt-get upgrade -y` - to upgrade relevant packages
- `sudo apt-get install nginx -y` - to install nginx
- `sudo sed -i 's+try_files $uri $uri/ =404;+proxy_pass http://localhost:3000/+;' /etc/nginx/sites-available/default` - To add proxy pass to default file within nginx.
- `sudo nginx -t` - To verify there are no syntax errors

- `sudo systemctl restart nginx` - To restart nginx

`sudo apt-get install git -y`

`curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`

`sudo apt-get install nodejs -y`

`npm install pm2 -g`

`cd app`

`npm install`

`npm start`
