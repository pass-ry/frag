UBUNTU18 v2rayl
bash <(curl -L -s https://install.direct/go.sh)

说明
此脚本会自动安装以下文件：
/usr/bin/v2ray/v2ray：V2Ray 程序；
/usr/bin/v2ray/v2ctl：V2Ray 工具；
/etc/v2ray/config.json：配置文件；
/usr/bin/v2ray/geoip.dat：IP 数据文件
/usr/bin/v2ray/geosite.dat：域名数据文件

根据你服务器端的配置来修改/etc/v2ray/config.json配置文件
{
"log": {
 "access": "",
"error": "",
"loglevel": "warning"
},
"inbounds": [
{
  "port": 1080,
  "listen": "127.0.0.1",
  "protocol": "socks",
  "sniffing": {
    "enabled": true,
    "destOverride": [
      "http",
      "tls"
    ]
  },
  "settings": {
    "auth": "noauth",
    "udp": true,
    "ip": null,
    "clients": null
  },
  "streamSettings": null
}
],
"outbounds": [
{
  "tag": "proxy",
  "protocol": "vmess",
  "settings": {
    "vnext": [
      {
        "address": "cc.*****.com",
        "port": 443,
        "users": [
          {
            "id": "**********",
            "alterId": 16,
            "email": "****",
            "security": "auto"
          }
        ]
      }
    ],
    "servers": null,
    "response": null
  },
  "streamSettings": {
    "network": "ws",
    "security": "tls",
    "tlsSettings": {
      "allowInsecure": true,
      "serverName": null
    },
    "tcpSettings": null,
    "kcpSettings": null,
    "wsSettings": {
      "connectionReuse": true,
      "path": "/qqgame",
      "headers": {
        "Host": "cc.acgjs.com"
      }
    },
    "httpSettings": null,
    "quicSettings": null
  },
  "mux": {
    "enabled": true
  }
},
{
  "tag": "direct",
  "protocol": "freedom",
  "settings": {
    "vnext": null,
    "servers": null,
    "response": null
  },
  "streamSettings": null,
  "mux": null
},
{
  "tag": "block",
  "protocol": "blackhole",
  "settings": {
    "vnext": null,
    "servers": null,
    "response": {
      "type": "http"
    }
  },
  "streamSettings": null,
  "mux": null
}
],
"dns": null,
"routing": {
"domainStrategy": "IPIfNonMatch",
"rules": []
}
}


// 启动
service v2ray start

//查看状态
service v2ray status


// 配置代理
手动 > socks：127.0.0.1:1080 > 忽略主机 localhost， 127.0.0.0/8，::1
