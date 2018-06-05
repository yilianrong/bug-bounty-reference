# Guide to Basic Recon

Refer: https://blog.securitybreached.org/2017/11/25/guide-to-basic-recon-for-bugbounty/

Refer: https://hussnainfareed.wordpress.com/2017/11/25/guide-to-basic-reconnaissance-bug-bounties/

### No.1. Most Important

Properly read the terms for the bounty and clearly understand which domains are in scope and which forms of vulnerabilities are 
considered valid reposrts.

> **NOTE:** Submitting things that aren't within scope of the bounty program, tells the people running the program that you 
haven't properly read the terms, and it will lead to them not taking your future reports seriously.

### No.2. Map out the Target

Effectively map out most of the things you can do to get to know more about your target, how everything is structed and how 
everything works on the target.

> **NOTE:** You shold make notes during the recon to avoid confusion. Take them in whatever manner you want, but since 
participation in bug bounty programs involves mainly black box testing, it is really important to get a feel of how the site is 
structured and to map it all out in order to be able to effectively find bugs.

- Take the information like **Whois**, **Social Accounts**.

- Enumerate valid **subdomains**.

- **Port** scanning. Run a scan through nmap for limited ports, selected one or maybe 1-50000.

- Look for any **services** running on unusual ports or any service running on default ports which could be vulnerable (FTP, SSH,
etc). You're also going to want to look for the **version info** on services running in order to determine whether anything is 
outdeated and potentially vulnerable.

- Try extracting **vhosts**.

- Look at the **headers** to see which security options are in place, for example, looking for presence of X-XSS-Protection: or 
X-Frame-Options: deny. Knowing what security measures are in place means you know your limitations.

- Also look out for **WAFs**.

- Use **robots.txt** to determine the directories which may contain useful info, look for the disallow rules.

- **Burp Suite**, **spider** is going to be your best friend. Just make sure that your scope is set correctly so that you're not 
wasting time spidering unneeded domains. Also, **intruder** is completely necessary for directory brute-forcing. If you have
**Burp Suite Pro**, I highly recommend utilizing the **Reflector extension**. This will show you any parameters that are 
reflected into the response as Burp is spidering.

- Also spider the host for **API endpoints**.

- Extracting **S3 buckets** during recon is really nice idea, look for them manually or use tools.

> **NOTE:** Until now, stepwise notes typically contains:  **Whois Information**, **Subdomains**, **Dir info**, **S3 Buckets**,
**Social Accounts**, **API Endpoints**, **Emails**, **Vhosts**, **Backend IP address**, **Open Ports / Services Running**, 
**Service Version Ifo**, **Server Banners**, **Directory Listings**, **Presence Security Headers**, **WAF (+ WAF type)**.

- Make and capture requests and responses.

- Use google dorks, you can make your own or use made by others.

- Search github or pastebin for the company name and stumble across some random source that ended up online after some sloppy 
dev wrote it.

- Look deep into js files, manually or use tools.

- Look for older content that can give you ideas of site structure or maybe vuln endpoints.

- Maybe reversewhois lookup will help to discover more potential targets but make sure that they are in scope.

- Take a few minutes to look around PunkSpider.
