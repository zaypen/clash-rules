# Web Service Address Sets

## Address Sets

| Name | Type | Filename |
| - | - | - |
| AWS CloudFront | CIDR | aws-cloudfront-cidr.txt |
| Cloudflare | CIDR | cloudflare-cidr.txt |
| Fastly | CIDR | fastly-cidr.txt |

## Access via CDN (jsDelivr)

Format: 
```
https://cdn.jsdelivr.net/gh/zaypen/web-service-address-sets@release/<Filename>
```

Example - Cloudflare:

```
https://cdn.jsdelivr.net/gh/zaypen/web-service-address-sets@release/cloudflare-cidr.txt
```

## Use cases

### Clash

```yaml
rules:
  - RULE-SET,ad,REJECT
  - RULE-SET,gfw,PROXY
  - RULE-SET,cloudflare,DIRECT
  - GEOIP,LAN,DIRECT
  - GEOIP,CN,DIRECT
  - MATCH,PROXY

rule-providers:
  cloudflare:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/zaypen/web-service-address-sets@release/cloudflare-cidr.txt"
    format: 'text'
    path: ./ruleset/cloudflare.txt
    interval: 86400
```
