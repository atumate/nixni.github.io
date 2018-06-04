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

## shell code
``` sh

```
