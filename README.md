# Web Service Address Sets

## Address Sets

| Name | Type | Filename |
| - | - | - |
| AWS CloudFront | CIDR | aws-cloudfront-cidr.txt |

## Access via CDN (jsDelivr)

Format: 
```
https://cdn.jsdelivr.net/gh/zaypen/web-service-address-sets@release/<Filename>
```

### AWS Cloudfront CIDR

```
https://cdn.jsdelivr.net/gh/zaypen/web-service-address-sets@release/aws-cloudfront-cidr.txt
```

## Use cases

### Clash

```yaml
rules:
  - RULE-SET,ad,REJECT
  - RULE-SET,gfw,PROXY
  - RULE-SET,aws-cloudfront,DIRECT
  - GEOIP,LAN,DIRECT
  - GEOIP,CN,DIRECT
  - MATCH,PROXY

rule-providers:
  aws-cloudfront:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/zaypen/web-service-address-sets@release/aws-cloudfront-cidr.txt"
    format: 'text'
    path: ./ruleset/cloudfront.txt
    interval: 86400
```
