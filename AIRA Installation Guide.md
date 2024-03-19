# AIRA Installation Guide

## Overview

The AIRA installation guide provides step-by-step instructions for deploying AIRA, an enterprise-level application, on **CentOS/RHEL 8.x** using NGINX as the web server. The guide emphasises the importance of checking system requirements and ensuring an active internet connection for downloading necessary components.

|     AIRA Version    |             Platform             | Notes |
|:-------------------:|:--------------------------------:|:-----:|
| aira_build_08012024 | CentOS/RHEL 7.x | [Stack](https://github.com/airacommunity/AIRA-Documentation/blob/main/AIRA%20Server%20Configuration%20Setup.md) |

Before installing AIRA, check the Installation Requirements to determine whether your server meets the necessary hardware and software requirements. Ensure you have an Internet connection to download any necessary third-party components that your AIRA installation might require.

## Step 1 : Download AIRA Enterprise
Before proceeding with the installation, ensure that your server meets the hardware and software requirements outlined in the installation guide.

Open a terminal on your CentOS/RHEL 7.x server.

Download the AIRA Enterprise package from the specified link. You can use a tool like wget to retrieve the file directly to your server:

```
wget Link
```

Wait for the download to complete. This process may take some time, depending on your internet connection speed.

Once the download is finished, you should have the AIRA package file in your current working directory, ready for extraction in the next installation steps.

Ensure that you have an active internet connection during this step to fetch the necessary files. Verify the integrity of the downloaded package by checking its size or using any provided checksums if available.

## Step 2: Extract AIRA Zip File

Extract the AIRA zip file using the unzip command. Ensure to specify the source file (AIRA zip file) and the destination directory (/opt/aira/ in this case):
```
unzip aira_build_08012024.zip -d /opt/aira/
```

Verify that AIRA was decompressed successfully. You can use the ls command to list the contents of the /opt/aira/ directory:

```
ls /opt/aira/
```

Ensure that the extracted files and directories are visible in the specified location.

By following these steps, you should have successfully extracted the AIRA zip file into the designated directory /opt/aira/.

## Step 3: Set File Permissions

Set the NGINX user (`nginx`) as the owner for all AIRA files and directories using the `chown` command:

```
chown -R nginx:nginx /opt/aira
```
  
This recursively changes the ownership of all files and subdirectories within `/opt/aira/` to the NGINX user.

Verify the changes by checking the permissions and owner of the AIRA directory using the `ls` command:

```
ls -l /opt/aira/core/
```

Ensure that the output reflects the new ownership, and all files are owned by the NGINX user (`nginx`). The result should resemble something like:

## Step 4 : Install Node Modules of Backend and Start Conductor Commands

### 1. Navigate to the core directory:

```
cd /apps/aira/core/
```

### 2. Create an environment file:

```
sudo nano .env
```

Populate the `.env` file with the required environment variables.

```
PORT=
HOST=
NODE_ENV=
APP_KEY=GTdsiVloh3zSeiCkDOLo7LNBdrPSQBY9
DRIVE_DISK=local
DB_CONNECTION=
MYSQL_HOST=
MYSQL_PORT=
MYSQL_USER=
MYSQL_PASSWORD=
MYSQL_DB_NAME=
CONDUCTOR_URL=
GOOGLE_API_URL=https://www.googleapis.com/
GOOGLE_ACCOUNT_URL=https://accounts.google.com/
GOOGLE_SHEET_DRIVE=https://sheets.googleapis.com/v4/
GOOLGE_FCM=https://fcm.googleapis.com/v1/
ACTIVITY_FOLDER=activity
LOG_PATH= /tmp/
FILE_PATH=/tmp/jobs/
PORTAL_FILE_PATH=
SMTP_HOST=
SMTP_PORT=
SMTP_USERNAME=
SMTP_PASSWORD=
MAIL_FROM_EMAIL=
CACHE_VIEWS=false
MAIL_EXPIRY_MIN=10
MAILCHIMP_HOST=
AIRA_URL=
GUEST_USER = 'guest@aira.fr'
JWT_PRIVATE_KEY=-----BEGIN PRIVATE KEY-----\n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\nbwm4DI6XIpJtt28IJTwVAYQ6oKSSGZs=\n-----END PRIVATE KEY-----\n
JWT_PUBLIC_KEY=-----BEGIN PUBLIC KEY-----\nMIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAxlv9I5CYaQfOCVGcNDse\ntYtvh2NL1wjQRSWKU/qcCtwaU6TjNWc45jc0bNHBKT0zkzGlMJ4tatsS41w19e4b\n6TgpI7sUpkQy5tKPOwDEucl+hGQosrwUhMJ+kjS4zmyzd5EbNa5anOuPXliGaYUi\nurQrb3MsBLD+3rXKY4yL7SCX2vNDanfd6QU3J3V1Y6n+HGxTSPDHdhGdIxD1hsQP\n9u/aHEPUxGpWgMWf3HHDE0jzrWirtMhJ87Xx0dDiTfO8ru4/uwgW8qSVL8Bf5Ecc\nAQu6VrZ8ew0iSnz3w+5GRPoTPJsIYS1WRCub6ihlNW3fS1o8fs0gE0SSp0WZcHLq\nyglk5wwZvGNUs78WZvEQHKTESdeDJmCPuwJP0/+769+rpqAIljRTlrlBdrFAbf6l\nMggY+LsY8RX3YvEhijQaYyu/DD1C60nR974P/JoTBmIiim/kRUUOP6npSaIeMLEq\nNXCE50ann3J2a0dftIjU/377A5Jcs6zqoKy/Iq85WSY5qsCxSEymnskgVFTNz0hZ\nQsqY5ykJ8c8qGOj3hdKObSIV91bfeFcTLCz2PDEN7vbivOganjtydSGfE3SKpt9N\nyBFTZig+IHQWMhQ7W3xbkg470GEhIv+pYA+J41sSux8cMB2EqFyWJ/iLbMa57duF\nMaaGDHWaAw0au8aMpCkQqjMCAwEAAQ==\n-----END PUBLIC KEY-----\n
CRON_FILE_NAME=
SESSION_DRIVER=cookie
```

### 3. Run migrations:

```
node ace migration:run
```

### 4. Seed the database:

```
node ace db:seed
```

### 5. Install npm dependencies:

```
sudo npm install
sudo npm ci --production
```

### 6. Install PM2 globally:

```
npm install pm2 -g
```

### 7. Check if the Node server is running without errors:

```
node server.js
```

**Note : Press ctrl + c to exit**

### 8. Register the app in PM2 for background service:

```
pm2 start "node server.js" --name "app_name"
```

## Orchestration Engine Setup:

### 1. Navigate to the systemd service directory:

```
cd /etc/systemd/system/
```

### 2. Create a conductor.service file:

```
sudo nano conductor.service
```

### 3. Upload File and Save it.

```
[Unit]
Description=Conductor service
Requires=network.target remote-fs.target
After=network.target remote-fs.target


[Service]
Type=simple
User=root
WorkingDirectory=/opt/aira/conductor/
ExecStart=/usr/bin/java -jar /opt/aira/conductor/conductor-server-3.3.4-boot.jar --conductor.db.type=mysql --spring.datasource.url=jdbc:mysql://your-ip:3306/conductor --spring.datasource.username=root --spring.datasource.password= --debug=enabled
Restart=on-failure
RestartSec=10


[Install]
WantedBy=multi-user.target
```

### 3. Enable and start the orchestration engine service:

```
systemctl enable conductor.service
systemctl start conductor.service
```

### 4. Check the status of the orchestration engine service:

```
systemctl status conductor.service
```

### 5. Verify the orchestration engine in the browser:

```
Visit http://your-ip:8080/
```

## Stop Server and Create DMS Folders:

### 1. Create folders for DMS in the core directory:

```
cd /opt/aira/core/
mkdir public
mkdir storage
```

### 2. Navigate to the storage directory and create subdirectories:

```
cd /opt/aira/core/storage/
mkdir output
mkdir input
mkdir assets
```

### 3. Create Symbolic Link after folder creation.

```
ln -s /opt/aira/core/idp/ /opt/aira/core/public/
ln -s /apps/aira/core/storage/ /apps/aira/core/public/
```

## Step 5: NGINX Configuration

Create a configuration file inside /etc/nginx/conf.d/ with the command:

```
nano /etc/nginx/conf.d/aira.conf
```

If using an SSL certification, follow these steps to do the configuration of NGINX:

### 1. In the created file the configuration file should be as follows:

```
server {
         listen 80;
         listen [::]:80;
         return 301 https://localhost$request_uri;
                }
server {
        listen              443 ssl;
        server_name        localhost;
        keepalive_timeout   300;
        proxy_read_timeout 300;
        proxy_connect_timeout 300;
        proxy_send_timeout 300;

        ssl_certificate     /etc/nginx/ssl/<certificate file>.cert;
        ssl_certificate_key /etc/nginx/ssl/<certificate key>.key;

        ssl_protocols       TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
        ssl_ciphers         HIGH:!aNULL:!MD5;
        root /opt/aira;
        client_max_body_size 100M;
     index index.html index.htm index.html inde.php;
         #index index.php;
        location /assets {
          proxy_pass http://localhost:8000/;
        }
        location /api/v1 {
                proxy_pass http://localhost:8000/api/v1;
                proxy_set_header Host $host;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                #proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-Proto $scheme;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

                proxy_cache_bypass $http_upgrade;
        }
        location / {
        #index index.html index.htm index.html inde.php;
       # autoindex on;
       # autoindex_exact_size off;
        if (!-e $request_filename){
                rewrite ^(.*)$ /index.html break;
         }
        }
}

```

### 2. On the same file, change the localhost attribute with the IP of your server as an example:

```
localhost 192.168.1.100;
```

### 3. Reset the nginx server:

```
service nginx restart
```

## Step 6: Install AIRA

### 1. After completing the stack configurations and setting file permissions, open a web browser on your client machine.

### 2. Enter the IP address of your server in the address bar, followed by the port number corresponding to your configuration. If using default ports:

  * For SSL configuration (Port 443)
    If you specified custom ports during NGINX configuration, adjust the URL accordingly.
    ```
    https://<server_ip>
    ```

  * If AIRA is installed locally at port 8888, use:
    ```
    https://127.0.0.1:8888
    ```

Enter the IP address of your server in the address bar, followed by the corresponding port numbers. If using default ports:

## Conclusion
Congratulations! You have successfully completed the installation of AIRA on your CentOS/RHEL 7.x server. By following the provided steps, you've configured the necessary components, set file permissions, and accessed the AIRA installation wizard to finalise the setup.

As you proceed, it is essential to regularly check for updates, security patches, and any additional configuration requirements for optimal performance and security. Refer to the official AIRA documentation for any post-installation tasks, maintenance guidelines, or troubleshooting tips.

Feel free to explore the features and capabilities of AIRA through the web interface. If you encounter any issues, consult the provided installation guide or the official support channels for assistance.

Thank you for choosing AIRA. If you have any further questions or need additional support, don't hesitate to refer to the documentation or seek help from the AIRA community.

Happy exploring and utilising AIRA for your enterprise needs!




