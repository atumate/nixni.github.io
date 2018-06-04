
## Make it work
1. `wget https://bootstrap.pypa.io/get-pip.py && python get-pip.py`
1. `pip install shadowsocks`
1. `sslocal -s ip -p 443 -k "code" -l 1080 -m aes-256-cfb`
1. `chkconfig shadowsocks on && service shadowsocks start`
1. `curl --socks5 127.0.0.1:1080 ip.cn` 
1. `yum -y install privoxy`
1. `cp /etc/privoxy/config /etc/privoxy/config_bak`
1. ensure below lines are not commented, line1 usually not, line2 need modify
	```
	listen-address 127.0.0.1:8118 
	forward-socks5t / 127.0.0.1:1080 . 
	```
1. run below in bash
	```
	export http_proxy=http://127.0.0.1:8118
	export https_proxy=http://127.0.0.1:8118
	```
1. `chkconfig privoxy on && service privoxy start`
1. `curl ip.cn` 

## Let it elegant
save below code to a file like `setproxy`, then `. setproxy on` means open,`. setproxy on` means shutdown


```bash
#!/bin/bash


if [ "$1" == "on" ]; then
        service privoxy start

        export http_proxy=http://127.0.0.1:8118
        export https_proxy=http://127.0.0.1:8118
        # /root/bin/slsl back  # this line start socks client
elif [ "$1" == "off" ]; then
        export http_proxy=""
        export https_proxy=""
        service privoxy stop
elif [ "$1" == "status" ]; then
        service privoxy status
else
        echo 'Please input argument: on,off,status'
fi

echo 'Now your ip is: '
curl ipinfo.io
echo ''

```
