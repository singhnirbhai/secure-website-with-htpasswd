# # How HTPasswd secure your website.

## Step 1: Install Required Tools

```bash
yum install httpd-tools
```

## Step 2: Create the htpasswd File

```bash
htpasswd -c /etc/httpd/.htpasswd username
```

## Step 3: Configure Apache Authentication

## Create the Configuration file in /etc/httpd/config.d directory.

```bash
vi /etc/httpd/conf.d/httpd.conf
```

Copy the full entry form (<Directory) and paste inside file :
 ##  <Directory "/var/www/html">
    AuthType Basic
    AuthName "Protected Directory"
    AuthUserFile /etc/httpd/.htpasswd
    Require valid-user
    AllowOverride All
 ## </Directory>

## Step 4: Set Proper File Permissions:

```bash
chmod 644 /etc/httpd/.htpasswd
```
Make htpasswd file readable by Apache but not accessible from web.

```bash
chown root:apache /etc/httpd/.htpasswd
```
Change the groupownership permission to the apache group.

## Step 5: Restart Apache Service:

```bash
 systemctl restart httpd
 ```

 ## Step 6: Test Your Setup:

1.Open a web browser and navigate to your protected directory

2.You should see a login prompt asking for username and password

3.Enter the credentials you created with htpasswd

4.Successful authentication should grant access to the protected  content 

