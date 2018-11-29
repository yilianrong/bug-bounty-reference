# Guide to Basic Recon

### 1. read rules and scope, understand the function of the website

#### 1.1. sitemap

public pages, we can access without a user account

private pages, only accessible with a user account

- [visualsitemapper](http://www.visualsitemapper.com/)

### 2. for scope

#### 2.1. www.domain.com

2.1.1. check robots.txt

2.1.2. enumerate subdirectory

- [dirsearch](https://github.com/maurosoria/dirsearch) + [SecLists](https://github.com/danielmiessler/SecLists)

#### 2.2. **.domain.com

2.2.1. enumerate subdomain

- [Sublist3r](https://github.com/aboul3la/Sublist3r)
- [crt.sh](https://crt.sh/)

2.2.2. subdomain takeover

- [Fingerprint for specific engine](https://github.com/EdOverflow/can-i-take-over-xyz)

### 3. for asserts

#### 3.1. S3 buckets

query S3 buckets and search sensitive information or try to replace resource

- [bucket-stream](https://github.com/eth0izzle/bucket-stream)
- [AWSBucketDump](https://github.com/jordanpotti/AWSBucketDump)

#### 3.2. github

query github and search sensitive information suck as keys

- [truffleHog](https://github.com/dxa4481/truffleHog)

#### 3.3. JS

use burpsuite to extract all JS scripts

extract URL endpoints stored in JS scripts

#### 3.4. hidden Get & Post parameters

find hidden Get & Post parameters

- [Arjun](https://github.com/s0md3v/Arjun)

### 4. figer out WAF / CMS / Framework / template engine

- plugin Wappalyzer
- [wafw00f](https://github.com/EnableSecurity/wafw00f)

### 5. google docker

most useful: identify interesting files

if files is document type, use tools to extract metadata

### 6. whois

#### 6.1. whois lookup

- [domaintool](http://whois.domaintools.com/)
- [arintool](https://www.arin.net/resources/services/whois_guide.html)
- [radbtool](http://www.radb.net/support/query1.php)

#### 6.2. reverse ip lookup

- bing search: ip:192.239.213.197
- [yougetsignal](https://www.yougetsignal.com/tools/web-sites-on-web-server/)
- [ipaddress](https://www.ip-address.org/reverse-lookup/reverse-ip.php)
- [ipapi](http://ip-api.com/)

### 7. SSL/TLS certificates information

- [certificates information](https://www.certificate-transparency.org/known-logs)
- [censys-enumeration](https://github.com/yamakira/censys-enumeration)
- [CloudFlair](https://github.com/christophetd/CloudFlair)

### 8. shodan.io / censys.io

search device, like WAF
