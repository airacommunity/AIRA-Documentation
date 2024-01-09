# AIRA Installation Guide

## Overview
The AIRA installation guide provides step-by-step instructions for deploying AIRA, an enterprise-level application, on CentOS/RHEL 7.x using NGINX as the web server. The guide emphasises the importance of checking system requirements and ensuring an active internet connection for downloading necessary components.

| AIRA Version    | Platform |Notes |
| -------- | ------- | ------- |
| aira_build_08012024  |CentOS/RHEL 7.x (Latest version) |Stack  |

Before installing AIRA, check the Installation Requirements to determine whether your server meets the necessary hardware and software requirements. Ensure you have an Internet connection to download any necessary third-party components that your AIRA installation might require.

### Step 1 : Download AIRA Enterprise
Before proceeding with the installation, ensure that your server meets the hardware and software requirements outlined in the installation guide.

Open a terminal on your CentOS/RHEL 7.x server.

Download the AIRA Enterprise package from the specified link. You can use a tool like wget to retrieve the file directly to your server:
```
wget Link
```
Wait for the download to complete. This process may take some time, depending on your internet connection speed.

Once the download is finished, you should have the AIRA package file in your current working directory, ready for extraction in the next installation steps.

Ensure that you have an active internet connection during this step to fetch the necessary files. Verify the integrity of the downloaded package by checking its size or using any provided checksums if available.

### Step 2: Extract AIRA Zip File

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

### Step 3: Set File Permissions
Set the NGINX user (`nginx`) as the owner for all AIRA files and directories using the `chown` command:
```
chown -R nginx:nginx /opt/aira
```
  
This recursively changes the ownership of all files and subdirectories within `/opt/aira/` to the NGINX user.

Verify the changes by checking the permissions and owner of the AIRA directory using the `ls` command:
```
ls -l /opt/aira
```

Ensure that the output reflects the new ownership, and all files are owned by the NGINX user (`nginx`). The result should resemble something like:

### Step 4: NGINX Configuration
Create a configuration file inside /etc/nginx/conf.d/ with the command:
```
nano /etc/nginx/conf.d/aira.conf
```

If using an SSL certification, follow these steps to do the configuration of NGINX:

1. In the created file the configuration file should be as follows:
```
$ mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bk
$ nano /etc/nginx/nginx.conf
			user nginx;
 
			worker_processes auto;
			 
			error_log  /var/log/nginx/error.log warn;
			 
			pid       /var/run/nginx.pid;
			 
			# Load dynamic modules. See /usr/share/nginx/README.dynamic.
			 
			include /usr/share/nginx/modules/*.conf;
			 
			events {
			  worker_connections 1024;
			}
			 
			http {
			  include        /etc/nginx/mime.types;
			  default_type   application/octet-stream;
			  log_format     main '$remote_addr - $remote_user [$time_local] "$request" '
								  '$status $body_bytes_sent "$http_referer" '
								  '"$http_user_agent" "$http_x_forwarded_for"';
			  access_log  /var/log/nginx/access.log  main;
			  log_format combined_ssl '$remote_addr - $remote_user [$time_local] '
									  '$ssl_protocol/$ssl_cipher '
									  '"$request" $status $body_bytes_sent '
									  '"$http_referer" "$http_user_agent"';
			  sendfile            on;
			  tcp_nopush          on;
			  tcp_nodelay         on;
			  keepalive_timeout   120;
			  keepalive_requests  100;
			  types_hash_max_size 2048;
			 
			  #Enable Compression
			  gzip on;
			  gzip_disable "msie6";
			  gzip_vary on;
			  gzip_proxied any;
			  gzip_comp_level 6;
			  gzip_buffers 16 8k;
			  gzip_http_version 1.1;
			  gzip_types text/css text/plain text/xml text/x-component text/javascript application/x-javascript application/javascript application/json application/xml application/xhtml+xml application/x-font-ttf application/x-font-opentype application/x-font-truetype image/svg+xml image/x-icon image/vnd.microsoft.icon font/ttf font/eot font/otf font/opentype;
			 
			  include /etc/nginx/conf.d/*.conf;
			  
			 
			  #Comment out ServerTokens OS
			  server_tokens off;
			 
			  #Prevent ClickJacking Attacks
			  add_header X-Frame-Options SAMEORIGIN;
			 
			  #Load Balancer/Reverse Proxy Header
			  real_ip_header X-Forwarded-For;
			  set_real_ip_from 0.0.0.0/0;
			}
			
$ systemctl restart nginx

```


2. On the same file, change the server_name attribute with the IP of your server as an example:
```
server_name 192.168.1.100;
```

3. Reset the nginx server:
```
service nginx restart
```
### Step 5: Install AIRA
1. After completing the stack configurations and setting file permissions, open a web browser on your client machine.

2. Enter the IP address of your server in the address bar, followed by the port number corresponding to your configuration. If using default ports:

For SSL configuration (Port 443)
If you specified custom ports during NGINX configuration, adjust the URL accordingly.
 ```
http://<server_ip>:443 
```

If AIRA is installed locally at port 8080, use:
```
http://127.0.0.1:8080 
```

Enter the IP address of your server in the address bar, followed by the corresponding port numbers. If using default ports:

For Port 8000:
```
http://<server_ip>:8000
```

For Port 5000:
```
http://<server_ip>:5000
```
### Conclusion
Congratulations! You have successfully completed the installation of AIRA on your CentOS/RHEL 7.x server. By following the provided steps, you've configured the necessary components, set file permissions, and accessed the AIRA installation wizard to finalise the setup.

As you proceed, it is essential to regularly check for updates, security patches, and any additional configuration requirements for optimal performance and security. Refer to the official AIRA documentation for any post-installation tasks, maintenance guidelines, or troubleshooting tips.

Feel free to explore the features and capabilities of AIRA through the web interface. If you encounter any issues, consult the provided installation guide or the official support channels for assistance.

Thank you for choosing AIRA. If you have any further questions or need additional support, don't hesitate to refer to the documentation or seek help from the AIRA community.

Happy exploring and utilising AIRA for your enterprise needs!


