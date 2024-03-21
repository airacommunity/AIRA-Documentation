# Overview

This guide provides detailed information on configuring the database and application server for installing AIRA on the CentOS/RHEL 7.x platform. The recommended stack has been thoroughly tested and is supported by the AIRA quality control team. The installation is intended for use with NGINX as the web server.


## Stack Components

<table>
  <tr>
    <td>Platform</td>
    <td>CentOS/RHEL 7.x </td>
  </tr>
  <tr>
    <td>Database</td>
    <td>MySQL 8.0</td>
  </tr>
  <tr>
    <td>Web Server</td>
    <td>NGINX 1.x.x (Latest version)</td>
  </tr>
  <tr>
    <td>Filesystem</td>
    <td>xfs</td>
  </tr>
  <tr>
    <td>Architecture</td>
    <td>64-bit</td>
  </tr>
</table>



> Disclaimer : The stack procedure outlined below has been successfully used in AIRA's cloud environment and is supported by the Quality Control team. However, if implemented on-premise by the client's IT staff, AIRA does not guarantee correct functionality.

## Preparing Stack For AIRA Installation

The following instructions can be used to prepare the stack for AIRA installation if you already have the most recent version of CentOS 7.x Core or Desktop installed, have the necessary rights (by typing sudo su and entering the administrator password), and have the necessary files.

> Kindly follow the steps that are given below to configure the server.

### Step 1 : Update Server

Make sure that your server is running the latest version. Below given command will update the system without requiring manual confirmation for each package update.

```
yum -y update
```
  
### Step 2 : Node Installation

This install Node.js, a JavaScript runtime, and npm (Node Package Manager), essential for running JavaScript-based applications.

  
```
$ curl -fsSL https://rpm.nodesource.com/setup_16.x | sudo bash -
$ sudo yum install -y nodejs
$ node -v
$ sudo yum install gcc-c++ make
```
### Step 3 : Yarn Installation

Yarn is a package manager for Node.js that efficiently manages project dependencies. This step installs Yarn on your system.

```
$ curl -sL https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo
$ sudo yum install yarn
```

### Step 5 : Remove MariaDB

By default CentOS 7.x comes with some modules of MariaDB installed so we have to remove MariaDB, a database management system.

```
$ yum -y remove mariadb*
```

### Step 6 : Install MySQL 8

These steps collectively install MySQL 8, make necessary adjustments to the repository configuration for smooth installation, start the MySQL service, and perform additional configuration by modifying the SQL mode. These configurations are crucial for the proper functioning of MySQL in the context of the AIRA server.

  
```
yum localinstall -y https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
yum install -y mysql-community-server
```
  

Start the MySQL service and set it to start automatically at boot.

  
```
$ systemctl start mysqld
$ systemctl enable mysqld
```
  

Make sure the mysql service is running by checking its status.

```
$ systemctl status mysqld
```
  

The status of the mysql service should be "active (running)".

  

![](https://lh7-us.googleusercontent.com/SSqD2Q0FUU9D37pZOL55TX1OV3aXGI6_gzOzCTI82MGGOfOU8K8YtaNtNIEkuNyGVMGWslwJYo82QE6trO5PyIuIr_1KmMa8MyevaTO6WZ2ZpfiNm-mwhhoJvyjWMPbJzUj-b2NMiOE70mASzSaxae0)

  

Modifies the global sql_mode setting in MySQL/MariaDB by removing the ONLY_FULL_GROUP_BY mode. This can be useful for avoiding strict SQL mode errors related to GROUP BY queries.

  
```
SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''));
```
### Step 7: MySQL Configuration

This set of commands outlines the MySQL configuration steps needed to secure the MySQL installation before using it in the context of the AIRA server.

#### Check Temporary Password:

Description: This command retrieves the temporary root password generated during the MySQL installation. It's essential to note and use this temporary password when executing subsequent configuration steps

  
```
$ grep "temporary password" /var/log/mysqld.log
```

#### Secure MySQL Installation:

Description: The mysql_secure_installation command initiates a series of interactive prompts to set up a secure MySQL environment. This includes:

-   Changing the temporary root password (if not expired).
-   Defining a new root password adhering to MySQL's password policy.
-   Removing anonymous users for improved security.
-   Disabling remote root login to prevent unauthorised access.
-   Removing the test database for a cleaner setup.
-   Reloading privilege tables to apply changes
    
```
$ mysql_secure_installation
```

> **Password Policy Warning:** The default password policy implemented by validate_password of MySQL 8.0 requires that passwords contain at least one upper case letter, one lower case letter, one digit, and one special character, and that the total password length is at least 8 characters. To know more about validate_password, see The Password Validation Plugin.

#### Turn off Derived Table Merging Flags:

This command modifies the MySQL configuration file to disable derived table merging. Derived table merging is a query optimization feature, and turning it off may be necessary for specific applications.

  
```
echo "optimizer_switch = derived_merge=off" >> /etc/my.cnf
```

#### Disable MySQL Strict Mode on the Server:

These commands append configuration lines to the MySQL configuration file, disabling strict mode. Strict mode enforces stricter interpretation of SQL standards, and turning it off can prevent certain errors or compatibility issues.

  
```
echo 'sql_mode = STRICT_TRANS_TABLES,NO_ZERO_IN_DATE' >> /etc/my.cnf
```

#### Restart MySQL Service:

Below given command restarts the MySQL service to apply the changes made to the configuration.

  
```
systemctl restart mysqld
```

### Step 8 : Install NGINX

The following set of commands and configurations is dedicated to installing NGINX, a popular web server, on a CentOS 7 system.

#### Create NGINX Repository Configuration File

Opens the Nano text editor to create or edit the NGINX repository configuration file.

  
```
$ nano /etc/yum.repos.d/nginx.repo
```

### Add NGINX Repository Information

Adds NGINX repository information to the configuration file, specifying the repository name, base URL for the NGINX packages, and disabling GPG signature checking (gpgcheck=0).
```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/rhel/8/$basearch/
gpgcheck=0
enabled=1
```

### Clean YUM Cache and Install NGINX

-   yum clean all: Clears the YUM package manager's cache, ensuring that the latest package information is fetched.
-   yum -y install nginx: Installs NGINX on the system.
    
``
$ yum clean all && yum -y install nginx
``
#### Start NGINX Service

Initiates the NGINX service, starting the web server.

```
$ systemctl start nginx
```
### Enable Autostart for NGINX

Configures NGINX to start automatically at system boot, ensuring that the web server is always available

```
$ systemctl enable nginx
```
### Step 9 :NGINX Server Configuration

The provided set of commands and configurations are part of the NGINX server configuration on a Linux system, specifically for CentOS.

#### Backup the Existing NGINX Configuration

This command creates a backup (nginx.conf.bk) of the existing NGINX configuration file (nginx.conf). It's a good practice to have a backup before making any significant changes.

```
$ mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bk
```
#### Edit NGINX Configuration

This command opens the NGINX configuration file (nginx.conf) for editing using the nano text editor. The subsequent lines are part of the NGINX configuration and are added or modified as necessary.

```
$ nano /etc/nginx/nginx.conf
```
#### NGINX Configuration Block

This section represents the NGINX configuration block. It includes settings related to user permissions, worker processes, logging formats, compression, and more. Notable configurations include enabling gzip compression, setting log formats, and enhancing security by disabling server tokens and preventing ClickJacking attacks.

```
user nginx;
worker_processes auto;

error_log  /var/log/nginx/error.log warn;
pid /var/run/nginx.pid;

include /usr/share/nginx/modules/*.conf;

events {
  worker_connections 1024;
}

http {
  include  /etc/nginx/mime.types;
  default_typeapplication/octet-stream;

  log_format  main '$remote_addr $remote_user [$time_local] "$request" '
 '$status $body_bytes_sent "$http_referer" '
 '"$http_user_agent" "$http_x_forwarded_for"';

  access_log  /var/log/nginx/access.log  main;

  log_format combined_ssl '$remote_addr $remote_user [$time_local] '
  '$ssl_protocol/$ssl_cipher '
  '"$request" $status $body_bytes_sent '
  '"$http_referer" "$http_user_agent"';

  sendfileon;
  tcp_nopush on;
  tcp_nodelayon;
  keepalive_timeout120;
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

```
#### Restart NGINX

After making changes to the NGINX configuration, this command restarts the NGINX service to apply the new configuration. This step is crucial for the changes to take effect.
```
$ systemctl restart nginx
```
## Step 9 :Remove Python 3 old version

This step involves removing the existing versions of Python 3 from the system. The command removes all files and directories related to Python 3, providing a clean slate for the installation of a specific Python version.

  
```
rm -rf /usr/lib/python3.*
```
### Step 10 :Install python 3.9

#### Install prerequisite

First, ensure that you have the necessary development tools and libraries installed on your system. These packages are necessary for compiling Python from source and ensuring that all dependencies are met.

  
```
$ sudo yum install gcc openssl-devel bzip2-devel libffi-devel zlib-devel
```
#### Download Python 3.9

Next, download the Python 3.9 source code from the official Python website. You can use the wget command to download the tarball directly to your system:

  
```
$ wget https://www.python.org/ftp/python/3.9.16/Python-3.9.16.tgz
```
#### Extract the Archive

Once the download is complete, extract the tarball using the following command. This will create a directory named Python-3.9.16 containing the Python source code.

  
```
$ tar xzf Python-3.9.16.tgz
```
### Install Python 3.9 on CentOS

Navigate into the extracted directory, configure the Python build with optimizations, and proceed with compiling and installing Python.

  
```
cd Python-3.9.16
sudo ./configure --enable-optimizations
sudo make altinstall
```
#### Clean Up

After installation, you can remove the downloaded source archive to save disk space.

```
$ sudo rm Python-3.9.16.tg`z
```
### Test Python Version

Finally, verify that Python 3.9 has been installed correctly by checking its version.

```  
$ python3.9 -V
```

### Open Bashrc and Set Python Version Alias

Open the Bash configuration file `~/.bashrc` using the `vi` editor with elevated privileges (`sudo`). For the sake of this guide we'll be using VI as my text editor, but feel free to use whichever editor you prefer.

  
```
sudo vi ~/.bashrc
```
  

Adds an alias to the Bash configuration, specifying that when the `python` command is used, it should refer to version 3.9 located at `/usr/local/bin/python3.9`.

  
```
alias python3="/usr/local/bin/python3.9"
```
  

Sources or reloads the Bash configuration to apply the changes immediately.

  
```
. ~/.bashrc
```
  

Check the version of Python to confirm that version 3.9 is now the default.

  
```
python -V
```

#### Install Python Libraries

Install various Python libraries using `python3 -m pip install`, including:

  
```
pip install transformers==4.25.0
pip install docquery==0.0.7
pip install tensorflow==2.12.0
pip install scikit-learn==1.1.3
pip install paddlepaddle==2.5.0 paddleocr==2.6.1.3
pip install ultralyticsplus==0.0.23 ultralytics==8.0.21
pip install pydantic==1.8.2
pip install ydata-profiling==4.1.1
pip install xgboost==1.7.4
Installs Poppler version 22.12.0
yum install poppler-utils= 22.12.0
Installs Tesseract OCR (Optical Character Recognition) version 4.1.1.
yum install tesseract=4.1.1
```

Exports an environment variable (`TESSDATA_PREFIX`) that specifies the path to Tesseract's tessdata directory.

```
export TESSDATA_PREFIX=/usr/share/tesseract/tessdata/
```

## Step 11 :Firewall Configuration

This step focuses on configuring the firewall settings on the CentOS system to ensure proper network access for the AIRA server. Here's a breakdown of the commands:

### Install and Start Firewalld

-   Installs the firewalld package, which is a dynamic firewall manager for Linux.
-   Starts the firewalld service immediately.
-   Configures firewalld to start at boot, ensuring it automatically starts on system reboot.
    

  
```
yum -y install firewalld
systemctl start firewalld
systemctl enable firewalld
```

### Open Required Ports in Firewall

-   Opens port 8080 for orchestrator engine API
-   Opens port 3306 for MySQL.
-   Opens port 443 (HTTPS) in the public zone permanently.
-   Reloads the firewall configuration to apply the changes
    

  
```
firewall-cmd --add-port=3306/tcp --permanent
firewall-cmd --zone=public --add-port=443/tcp --permanent
firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload
```

#### Disable SELinux for HTTP Network Connection

Adjusts the SELinux boolean to allow the Apache HTTP Server (`httpd`) to make network connections. This is necessary for the server to communicate over the network.
```
setsebool -P httpd_can_network_connect 1
```


#### Congratulations! You have successfully completed the configuration of the AIRA server. By following this guide. Remember to regularly update and maintain your server to ensure optimal performance and security.

