## Env
- CentOS 7.0
- Apache 2.4 installed by `yum -y install httpd`

## Step
1. `htpasswd -c /etc/httpd/.htpasswd user1` 
1. `vim /etc/httpd/conf/httpd.conf `, add below lines
    ``` httpd.conf
    <Directory "/var/www/html/dir-to-be-protected">
        Options +FollowSymLinks +Multiviews +Indexes
        AllowOverride None
        AuthType basic
        AuthName "private"
        AuthUserFile /etc/httpd/.htpasswd
        Require valid-user
    </Directory>
    ```
1. `service httpd restart`


## Refer
[https://wiki.apache.org/httpd/PasswordBasicAuth](https://wiki.apache.org/httpd/PasswordBasicAuth)
