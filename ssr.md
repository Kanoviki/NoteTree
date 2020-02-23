#SSR Installation Guide from YouTube
sudo apt install git python-m2crypto libsodium23
git clone https://github.com/shadowsocksrr/shadowsocksr.git
Get a sample configuration file on Github
	sudo vim /ect/shadowsocks.json <See Full Instruction on https://github.com/shadowsocksrr/shadowsocks-rss/wiki/Python-client-setup-(Multi-language) >
			'''
			{
                "server":"0.0.0.0",
                "server_ipv6": "::",
                "server_port":8388,
                "local_address": "127.0.0.1",
                "local_port":1080,
                "password":"mypassword",
                "timeout":300,
                "udp_timeout": 60,
                "method":"aes-256-cfb",
                "protocol": "auth_aes128_md5",
                "protocol_param": "",
                "obfs":"http_simple",
                "obfs_param": "",
                "fast_open": false,
                "workers": 1
            }
                
			'''
        Fill in values.
local.sh
	'''
	#!/bin/bash
	cd /home/"Your User Name"/shadowsocksr/shadowsocks
	python local.py -c /etc/shadowsocks.json -d start
	'''
stop.sh
	'''
	#!/bin/bash
	cd /home/"Your User Name"/shadowsocksr/shadowsocks
	python local.py -d stop
	'''
sudo chmod u+x local.sh stop.sh
sudo ./local.sh
	  **For firefox: change your proxy settings.**
	    In firefox Internet Settings, change yuor proxy to "socks5   server:127.0.0.1   port:1080"
	    socks5 DNS stategy.
sudo ./stop.sh
