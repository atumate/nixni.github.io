## basic tools
``` sh
yum -y install net-tools zip unzip vim elinks tree wget git curl
```

## ssh key login
``` sh
mkdir ~/.ssh && touch ~/.ssh/authorized_keys  && vim ~/.ssh/authorized_keys
```

## date sync
``` sh
yum install ntp -y
chkconfig ntpd on
ntpdate time.apple.com
```

## Timezone
``` sh
timedatectl set-timezone Asia/Shanghai
```

## epel
``` sh
yum install -y epel
```

## Docker
``` sh
yum install -y yum-utils 
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum makecache fast
yum -y install docker-ce
systemctl start docker
docker run hello-world
```

## shell code
``` sh

```
## LAMP
``` sh
yum install -y httpd mysql mariadb-server php php-mysql
chkconfig httpd on && chkconfig mariadb on
service httpd start && service mariadb start
firewall-cmd --permanent --zone=public --add-service=http && firewall-cmd --reload
```

## Samba
	yum install samba

smb.conf

	        security = user
	        passdb backend = tdbsam
	        # map to guest = bad user
	[w_html]
	        path = /var/www/html
	        browsable =yes
	        writable = yes
	        guest ok = yes
	        read only = no
	        force user = root
	        force group = root
		
---
	chkconfig smb on
	service smb start
	smbpasswd -a root


	firewall-cmd --permanent --zone=public --add-service=samba && firewall-cmd --reload


## LAMP + Samba config
	mkdir ~/config_files && cd config_files && ln -s /etc/httpd . && ln -s /etc/httpd/conf/httpd.conf . && ln -s /etc/samba/smb.conf .

## Selinux Apache
	chcon -R -t httpd_sys_content_t */

