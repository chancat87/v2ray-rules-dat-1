# v2ray-rules-dat
# Routing rule setting for the new releases of V2rayN
>This project is modified from [@Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat).The rule file format of the original project is too outdated, so it cannot be imported into the new version of V2rayN for use. Therefore, I will update the format of its Whitelist, Blacklist and DNS settings files. And  update and improve on it so that newbies can set their own proxy rules for the new release of V2ray. For more details on the rules, please visit the original project address, which will not be repeated in this project. For more advanced uses of V2rayN please visit the v2rayN project[@2dust/v2rayN](https://github.com/2dust/v2rayN), because it is not necessary to go into details in this project.

* To download the latest version of v2rayN, please visit https://github.com/2dust/v2rayN/releases
* To learn about the rules of the original project please visit https://github.com/Loyalsoldier/v2ray-rules-dat/releases
## WARNING:If you are new to V2rayN, or if you have an unknown error in your configuration, please move to [RELEASES](https://github.com/chenxv399/v2ray-rules-dat/releases) where V2rayN is already configured, open it and use it!!!
## The configured v2rayN has been updated to the latest v5.29 stable version on July 18, 2022, along with the updated system kernel and rule files.

## Dependency files GEO

>Before using the routing rules of this project, please download the enhanced versions of `geoip.dat` and `geosite.dat` and import them to the directory of v2rayN client, replacing the original `geoip.dat` and `geosite.dat`. Download at:


* `geoip.dat`

https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat 

* `geosite.dat`

https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat 

##The routing is configured as follows
First, you need to enable the Enable Route Advanced feature in the v2rayN routing settings, then double-click the rule you need to edit, and select Import Rule - Import Rule from Clipboard in the menu bar at the top of the pop-up window

Of course, if you have your own needs and know how to edit the code, it is perfectly possible to make changes to the following routing rules. If you wish to modify the geo configuration file, please visit https://github.com/Loyalsoldier/geoip
### Whitelist
Bypass mainland China, that is, all servers and IPs in mainland China are given priority to use the local network to connect directly, all other domains use vpn to connect
```
[
  {
    "port": "",
    "outboundTag": "proxy",
    "ip": [],
    "domain": [
      "geosite:geolocation-!cn",
      "github.com",
      "githubassets.com",
      "githubusercontent.com",
      "store.steampowered.com"
    ],
    "protocol": []
  },
  {
    "type": "field",
    "outboundTag": "block",
    "domain": [
      "mousegesturesapi.com",
      "cf-se.com",
      "geosite:category-ads-all",
      "googleads.g.doubleclick.net",
      "adservice.google.com"
    ]
  },
  {
    "type": "field",
    "port": "",
    "outboundTag": "direct",
    "ip": [
      "geoip:private",
      "geoip:cn",
    ],
    "domain": [
      "bitwarden.com",
      "bitwarden.net",
      "gravatar.com",
      "gstatic.com",
      "letsencrypt.org",
      "adblockplus.org",
      "safesugar.net",    
      "geosite:private",
      "geosite:cn",
      "geosite:adobe",
      "geosite:adobe-activation",
      "geosite:microsoft",
      "geosite:msn",
      "geosite:apple",
      "geosite:private",
      "geosite:apple-cn",
      "geosite:google-cn",
      "geosite:tld-cn",
      "geosite:category-games@cn"
    ],
    "protocol": []
  },
  {
    "type": "field",
    "port": "0-65535",
    "outboundTag": "proxy"
  }
]
```
### Blacklist
Blacklist, that is, the PAC connection in the old version of v2rayN, only sites known to be blocked priority through the vpn connection, the rest of all sites (regardless of China inside and outside China) are connected directly through the local network.
```
[
  {
    "outboundTag": "proxy",
    "domain": [
     "geosite:gfw",
     "geosite:greatfire",
    ]
  },
  {
    "outboundTag": "block",
    "domain": [
      "geosite:category-ads-all",
      "mousegesturesapi.com"
    ]
  },
  {
   "type": "field",
   "outboundTag": "Proxy",
   "ip": ["geoip:telegram"]
  },
  {
    "type": "field",
    "port": "0-65535",
    "outboundTag": "direct"
  }
]
```
## DNS Setting
settings-parameter settings-DNS settings-curl+v paste rule
* This is not necessary, the DNS setting is only for speeding up the loading of web pages, and it will not affect your normal internet connection if it is not set. So if you find that the code format copied to V2ranN does not match the format below, or simply reports an error that you cannot connect, please try clearing the DNS configuration first. At present, some devices are known to be messy after copying and pasting or report an unknown error after setting DNS.
```
{
  "hosts": {
    "dns.google": "8.8.8.8",
    "dns.pub": "119.29.29.29",
    "dns.alidns.com": "223.5.5.5",
    "geosite:category-ads-all": "127.0.0.1",
    "dns.cloudflare.com": "1.1.1.1",
    "aws.amazon.com":"169.254.169.253"
  },
  "servers": [
    {
      "address": "https://1.1.1.1/dns-query",
      "domains": ["geosite:geolocation-!cn"],
      "expectIPs": ["geoip:!cn"]
    },
    "8.8.8.8",
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

# Project Information Citation
[@Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)

[@2dust/v2rayN](https://github.com/2dust/v2rayN)

https://ivpsr.com/281.html

https://www.v2fly.org/config/dns.html#dnsobject

# Thanks
[@Loyalsoldier](https://github.com/Loyalsoldier)

[@2dust](https://github.com/2dust)
