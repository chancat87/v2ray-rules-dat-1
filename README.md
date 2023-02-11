# v2ray-rules-dat
# 新版V2rayN的路由规则设置
>本项目修改于[@Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat) 。因原项目的规则文件格式落后，导致无法导入新版的V2rayN中使用，故更新其Whitelist白名单、Blacklist黑名单和DNS setting DNS设置文件的格式，并在其基础上进行更新和改进，以便小白能够设置自己的新版V2ray的代理规则。更多规则细节请访问原项目地址，在本项目中不多赘述。想要了解V2rayN的更多高级用法请访问v2rayN的项目[@2dust/v2rayN](https://github.com/2dust/v2rayN) ，在本项目中也不过多赘述。

* 下载最新版v2rayN请访问https://github.com/2dust/v2rayN/releases
* 了解原项目作者的规则请访问https://github.com/Loyalsoldier/v2ray-rules-dat/releases
## 如果你是小白，或者你的配置出现了未知的错误，请移步[releases](https://github.com/chenxv399/v2ray-rules-dat/releases)，那里有已配置好的V2rayN，打开即用!!!
## 配置好的v2rayN已于2022年2月4日更新至最新v6.8版本，同时更新了系统内核和规则文件。当前版本有一个配置错误，详情参考[#7](https://github.com/chenxv399/v2ray-rules-dat/issues/7)

## 依赖GEO文件

>使用本项目的路由规则前，请先下载加强版的`geoip.dat`和`geosite.dat`，并导入到v2rayN客户端的目录，替换原来的`geoip.dat`和`geosite.dat`。下载地址：

* `geoip.dat`

https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat 

* `geosite.dat`

https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat 

**提醒：从v6.0版本开始，替换geo文件需要进入bin文件夹对所有支持路由规则的协议进行替换，包括`Xray` `SagerNet` `v2fly` `v2fly_v5`。推荐您每隔一个月手动更新一次geo文件。**

## 路由配置如下设置
首先需要开启v2rayN路由设置中的启用路由高级功能，随后在预定义规则集中双击需要编辑的规则集进行规则编辑。
**从v6.0版本开始，导入geoip和geosite文件后，白名单和黑名单的通用规则将自动写入，无需手动导入。如您有自定义的需求，可进入路由规则自行修改。**

#### 绕过大陆（白名单Whitelist）
绕过大陆，即所有服务器和ip在中国大陆的网站优先使用本地网络直接连接，所有其他的域名均使用vpn进行连接

#### 黑名单（Blacklist）
黑名单，即老版本v2rayN中的PAC连接，只有已知被墙的网站优先走vpn，其余所有网站（不管境内境外）均通过本地网络直连


## DNS配置如下设置
设置-参数设置-DNS设置-直接curl+v粘贴规则

**由于GFW的DNS污染加剧，强烈建议您设置此项。** 
如果设置后导致网络无法连接或者干脆无法保存设置，建议您使用上面已经配置好的v2rayN客户端，不要再手动折腾了。
```
 {
  "hosts": {
    "dns.google": "8.8.8.8",
    "dns.pub": "119.29.29.29",
    "dns.alidns.com": "223.5.5.5",
    "dns.opendns.com":"208.67.222.222",
    "geosite:category-ads-all": "127.0.0.1"
  },
  "servers": [
    {
      "address": "208.67.222.222",
      "port": 5353,
      "domains": ["geosite:geolocation-!cn"],
      "expectIPs": ["geoip:!cn"]
    },
    "8.8.8.8",
    "9.9.9.9",
    {
      "address": "114.114.114.114",
      "port": 53,
      "domains": ["geosite:cn", "geosite:category-games@cn"],
      "expectIPs": ["geoip:cn"],
      "skipFallback": true
    },
    {
      "address": "localhost",
      "skipFallback": true
    }
  ]
}
```

# 项目资料引用
[@Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)

[@2dust/v2rayN](https://github.com/2dust/v2rayN)

https://ivpsr.com/281.html

https://www.v2fly.org/config/dns.html#dnsobject

# 鸣谢
[@Loyalsoldier](https://github.com/Loyalsoldier)

[@2dust](https://github.com/2dust)
