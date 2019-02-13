# Bug Bounty Reference

A list of bug bounty write-up that is categorized by the bug nature, this is inspired by https://github.com/djadmin/awesome-bug-bounty

# Introduction

I have been reading for Bug Bounty write-ups for a few months, I found it extremely useful to read relevant write-up when I found a certain type of vulnerability that I have no idea how to exploit. Let say you found a RPO (Relativce Path Overwrite) in a website, but you have no idea how should you exploit that, then the perfect place to go would be [here](https://blog.innerht.ml/rpo-gadgets/). Or you have found your customer is using oauth mechanism but you have no idea how should we test it, the other perfect place to go would be [here](https://whitton.io/articles/obtaining-tokens-outlook-office-azure-account/)

My intention is to make a full and complete list of common vulnerability that are publicly disclosed bug bounty write-up, and let Bug Bounty Hunter to use this page as a reference when they want to gain some insight for a particular kind of vulnerability during Bug Hunting, feel free to submit pull request. Okay, enough for chit-chatting, let's get started. 


- [Cross-Site Scripting (XSS)](#cross-site-scripting-xss) done
- [Cross-Site Request Forgery (CSRF)](#cross-site-request-forgery-csrf) done
- [Server Side Request Forgery (SSRF)](#server-site-request-forgery-ssrf) done
- [XML External Entity (XXE)](#xml-external-entify-xxe) done
- [Insecure Direct Object Reference (IDOR)](#insecure-direct-object-reference-idor) done
- [Sensitive Information Exposure](#sensitive-information-exposure) done
- [Authentication Bypass](#authentication-bypass)
- [Stealing Access Token](#stealing-access-token) done
- [Business Logic Flaw](#business-logic-flaw) done
- [HTTP Header Injection](#http-header-injection) done
- [Subdomain Takeover](#subdomain-takeover) done
- [Local File Inclusion](#local-file-inclusion) done
- [Unrestricted File Upload](#unrestricted-file-upload) done
- [Brute Force](#brute-force) done
- [Race Condition](#race-condition) done
- [SQL Injection](#sql-injection) done
- [Remote Code Execution](#remote-code-execution) done
- [Miscellaneous](#miscellaneous) done
- [Exclusive Bugbounty Writeup Blog](#exclusive-bugbounty-writeup-blog) done
- [Interesting but Seems Not Applicable Now](#interesting-but-seems-not-applicable-now) done


### Cross-Site Scripting (XSS)

- [An XSS on Facebook via PNGs & Wonky Content Types](https://whitton.io/articles/xss-on-facebook-via-png-content-types/) by Jack Whitton
  - he is able to make stored XSS from a irrelevant domain to main facebook domain 
- [Stored XSSes in Facebook Wall by Embedding an External Video with Open Graph](https://opnsec.com/2018/03/stored-xss-on-facebook/) by Enguerran Gillier
- [XSS in Youtube, Google Translate, Google Docs](https://labs.detectify.com/2015/06/06/google-xss-turkey/) by fransrosen
- [Drag-Drop XSS in Google Docs Drawing Moudle](http://c0rni3sm.blogspot.com/2016/04/drag-drop-xss-in-google.html) by p0pc0rn
- [Subdomain Clickjacking in Google Trigger DOM XSS](http://sasi2103.blogspot.sg/2016/09/combination-of-techniques-lead-to-dom.html) by Sasi Levi
- [How I found a $5,000 Google Maps XSS (by fiddling with Protobuf)](https://medium.com/@marin_m/how-i-found-a-5-000-google-maps-xss-by-fiddling-with-protobuf-963ee0d9caff#.cktt61q9g) by Marin MoulinierFollow
- [Google Japan Book XSS](http://nootropic.me/blog/en/blog/2016/09/20/%E3%82%84%E3%81%AF%E3%82%8A%E3%83%8D%E3%83%83%E3%83%88%E3%82%B5%E3%83%BC%E3%83%95%E3%82%A3%E3%83%B3%E3%82%92%E3%81%97%E3%81%A6%E3%81%84%E3%81%9F%E3%82%89%E3%81%9F%E3%81%BE%E3%81%9F%E3%81%BEgoogle/)
- [App Maker and Colaboratory: a stored Google XSS double-bill](https://ysx.me.uk/app-maker-and-colaboratory-a-stored-google-xss-double-bill/) by Yasin Soliman
- [Stored XSS at Google firebase via Google Cloud IAM](http://panchocosil.blogspot.com/2017/04/stored-xss-at-google-firebase-via.html) by panchocosil
  - Two google products: `console.cloud.google.com` and `console.firebase.google.com`.
- [900$ XSS in yahoo ( Recon Wins )](https://medium.com/bugbountywriteup/900-xss-in-yahoo-recon-wins-65ee6d4bfcbd) by Th3G3nt3lman
  - Don't stop when you see the response forbidden/not found on the target you are testing, run dirsearch or any tool you prefer to find endpoints.
  - The author used Knoxss to identify the this XSS.
- [Love Story, From Closed As Informative to $3,500 USD, XSS Stored in Yahoo! iOS Mail App](http://omespino.com/write-up-lovestory-from-closed-as-informative-to-xx00-usd-in-yahoo-ios-mail-app/) by Omespino
- [XSS due to Improper Regex in Third Party JS in Uber](http://zhchbin.github.io/2016/09/10/A-Valuable-XSS/) by Chaobin Zhang
- [XSS in Uber via Cookie](http://zhchbin.github.io/2017/08/30/Uber-XSS-via-Cookie/) by Chaobin Zhang
- [Hijack the JS File of Uber's Website](http://zhchbin.github.io/2018/12/03/Hijack-the-JS-File-of-Uber-s-Website/) by Chaobin Zhang
  - Three writeups writen by Chaobin Zhang showed us "code review wins".
- [How I Discovered XSS that Affects around 20 Uber Subdomains](https://blog.fadyothman.com/how-i-discovered-xss-that-affects-over-20-uber-subdomains/) by Fady Othman
  - Using tool `https://www.samltool.com/decode.php`.
- [Airbnb – When Bypassing JSON Encoding, XSS Filter, WAF, CSP, and Auditor turns into Eight Vulnerabilities](https://buer.haus/2017/03/08/airbnb-when-bypassing-json-encoding-xss-filter-waf-csp-and-auditor-turns-into-eight-vulnerabilities/) by Brett Buerhaus
  - There are many tricks for bypassing.
- [Persistent XSS to Steal Passwords in Paypal](https://wesecureapp.com/blog/persistent-xss-to-steal-passwords-paypal/) by Akhil Reni
  - This vulnerability was found while tested different applications with third party integrations such as payment gateways, logging etc.
  - The author managed to exploit the worst case scenario.
  - The proc in this writeup is worth to study.
- [Turning Self-XSS into non-Self Stored-XSS via Authorization Issue at "PayPal Tech-Support and Brand Central Portal"](https://medium.com/@YoKoKho/turning-self-xss-into-non-self-stored-xss-via-authorization-issue-at-paypal-tech-support-and-brand-3046f52ac16b) by YoKo Kho
  - Complicated.
  - Two useful references by Brute: [File Upload XSS](https://brutelogic.com.br/blog/file-upload-xss/) and [Leveraging Self-XSS](https://brutelogic.com.br/blog/leveraging-self-xss/).
- [Use CSRF to Turn Self-XSS into XSS in A Browser's Extention by Indeed.com](http://c0rni3sm.blogspot.com/) by p0pc0rn
  - A vulnerability in a browser's extention.
- [The $12,000 Intersection between Clickjacking, XSS, and Denial of Service](https://samcurry.net/the-12000-intersection-between-clickjacking-xss-and-denial-of-service/) by samwcyo
  - The target itself is difficult to understand.
- [Coinbase AngularJS DOM XSS via Kiteworks](http://web.archive.org/web/20180410142546/http://www.paulosyibelo.com/2017/07/coinbase-angularjs-dom-xss-via-kiteworks.html) by Paulos Yibelo
  - Some thoeries about AngularJS seem difficult for a green to understand.
- [Unusual cases of reflected XSS](https://mike-n1.github.io/Unusual_XSS) by Script Kiddie
  - As the title stated, this writeup is about two unusual reflected XSSes.
- [How I found 5 store XSS on a private program. Each worth "1,016.66$"](http://cybristerboy.blogspot.com/2018/05/how-i-found-5-store-xss-on-private.html) by CybristerBoy
  - Intruder wins.
- [Reflected Client XSS at Amazon.com](https://medium.com/@jonathanbouman/reflected-client-xss-amazon-com-7b0d3cec787) by Jonathan Bouman
  - Extract the code from apk by using online decompiler: `http://www.javadecompilers.com/apk`, look around in the different files for urls to product pages.
  - Complicated.
- [How I found a persistent XSS affecting thousands of career sites](https://labs.detectify.com/2017/06/28/how-i-found-a-persistent-xss-affecting-thousands-of-career-sites/) by ak1t4
  - This is highly related to the bussiness logic, at this moment, I can't understand (because I didn't use the target's services).
- [Persistent Cross-Site Scripting on redacted worth $2,000](https://medium.com/@protector47/persistent-cross-site-scripting-on-redacted-worth-2-000-1e760617ccab) by M.Asim Shahzad
  - The target website was a CRM (what is CRM?). CRM based on Users and Admins, in case if the user-initiated XSS attack that affects admins and all users, that will be high-level XSS.
  - The author just searched for the *payloads and polyglots* to bypass the XSS filter.
- [Cookie Based Self-XSS to Good XSS](https://medium.com/@0xHyde/cookie-based-self-xss-to-good-xss-d0d1ca16dd0e) by hyde
  - The parenthesis characters were being filtered - bypass.
  - The payload couldn't be too many characters - bypass.

### Cross-Site Request Forgery (CSRF)

- [Hacking Facebook accounts using CSRF in Oculus-Facebook integration](https://www.josipfranjkovic.com/blog/hacking-facebook-oculus-integration-csrf) by JOSIP FRANJKOVIĆ
  - Oculus enables users to connect their Facebook accounts for more "social" experience, this can be done using both the native Windows Oculus application and using browsers.
  - The author found a CSRF vulnerability in the native Windows flow which allowed him to connect a victim's Facebook account to attacker's Oculus account. Once connected, the attacker could extract the victim's access token, and use Facebook's GraphQL queries to take over the account.
  - This vulenerability is complicated.
- [How i Hacked your Beats account ? Apple Bug Bounty](https://aadityapurani.com/2016/07/20/how-i-hacked-your-beats-account-apple-bug-bounty/) by Additya Purani
  - Complicated.

### Server Side Request Forgery (SSRF)

- [Pivoting from blind SSRF to RCE with HashiCorp Consul](http://www.kernelpicnic.net/2017/05/29/Pivoting-from-blind-SSRF-to-RCE-with-Hashicorp-Consul.html) by Peter Adkins
  - Complicated.
- [Blog post: Cracking the Lens: Targeting HTTP’s Hidden Attack-Surface ](https://portswigger.net/blog/cracking-the-lens-targeting-https-hidden-attack-surface) by James Kettle
  - Complicated.
- [Exploiting a Single Parameter](https://medium.com/@hisham.mir/exploiting-a-single-parameter-6f4ba2acf523) by Hisham Mir
  - The author bypassed many restrictions, but didn't explain in details, or maybe it is too abstract for me to understand.
- [AWS takeover through SSRF in JavaScript](http://10degres.net/aws-takeover-ssrf-javascript/) by Gwen
  - Javascript code reviewing wins.
- [Server-Side Request Forgery (SSRF) Attacks - Part 1: The basics](https://medium.com/poka-techblog/server-side-request-forgery-ssrf-attacks-part-1-the-basics-a42ba5cc244a) by Maxime Leblanc
- [Server-Side Request Forgery (SSRF) Attacks — Part 2: Fun with IPv4 addresses](https://medium.com/poka-techblog/server-side-request-forgery-ssrf-attacks-part-2-fun-with-ipv4-addresses-eb51971e476d) by Maxime Leblanc
- [Server-Side Request Forgery (SSRF) — Part 3: Other advanced techniques](https://medium.com/poka-techblog/server-side-request-forgery-ssrf-part-3-other-advanced-techniques-3f48cbcad27e) by Maxime Leblanc
 - This series is not as helpful as it seems.

### XML External Entity (XXE)

- [XML Entity Cheatsheet](https://www.silentrobots.com/blog/2015/12/14/xe-cheatsheet-update/) by silentrobots
- [How we got read access on Google’s production servers](https://blog.detectify.com/2014/04/11/how-we-got-read-access-on-googles-production-servers/) by  detectify
- [Blind OOB XXE At UBER 26+ Domains Hacked](http://nerdint.blogspot.hk/2016/08/blind-oob-xxe-at-uber-26-domains-hacked.html) by Raghav Bisht
- [0day in Code42 - XXE in uber.com to read local files](https://httpsonly.blogspot.com/2017/01/0day-writeup-xxe-in-ubercom.html) by httpsonly
- [Out of Band XML External Entity Injection via SAML SSO](https://seanmelia.files.wordpress.com/2016/01/out-of-band-xml-external-entity-injection-via-saml-redacted.pdf) by seanmelia
- [XXE by SVG in Lithium Community Platform](http://esoln.net/Research/2017/03/30/xxe-in-lithium-community-platform/) by Vibhuti Nath
- [Gainning Filesystem Access Via Blind OOB XXE](https://hawkinsecurity.com/2018/03/24/gaining-filesystem-access-via-blind-oob-xxe/) by tghawkins
- [How I Found CVE-2018-8819: Out-of-Band (OOB) XXE in WebCTRL](https://www.coalfire.com/The-Coalfire-Blog/June-2018/How-I-Found-CVE-2018-8819-Out-of-Band-(OOB)-XXE?feed=blogs) by Darrell Damstedt
- [Exploiting XXE with local DTD files](https://mohemiv.com/all/exploiting-xxe-with-local-dtd-files/) by Arseniy Sharoglazov
- [From blind XXE to root-level file read access](https://www.honoki.net/2018/12/from-blind-xxe-to-root-level-file-read-access/) by Honoki
- [Exploitation: XML External Entity (XXE) Injection](https://depthsecurity.com/blog/exploitation-xml-external-entity-xxe-injection) by Faisal Tameesh
  - I can't understand this type vulnerability so far.

### Insecure Direct Object Reference (IDOR)

- [View Insights for Any Facebook Marketplace Product](https://wongmjane.com/post/view-insights-for-any-fb-marketplace-product/) by Jane Manchun Wong
- [Dox Facebook Employees Behind “Did You Know” Questions](https://wongmjane.com/post/reveal-fb-employee-behind-funfact/) by Jane Manchun Wong
- [Disclose Facebook Internal Server Information With A Strange Poll](https://wongmjane.com/post/disclose-fb-intern-server-info-with-a-strange-poll/) by Jane Manchun Wong
  - In the previous three writeups the author used `GraphAPI` to extract sensitive information.
- [Airbnb – Web to App Phone Notification IDOR to view Everyone’s Airbnb Messages](https://buer.haus/2017/03/31/airbnb-web-to-app-phone-notification-idor-to-view-everyones-airbnb-messages/) by Brett Buerhaus
  - "Experiences" new feature allows you to book things to do rather than places to stay.
  - The author discovered a page that allowed you to sent yourself a text message with a link to download the Airbnb app. This sent a POST request to an API endpoint, using the JS Parser tool they built we discovered another API call associated with it. The author found that these API calls were vulnerable to IDOR and allowed you to view all messsages on Airbnb by ID.
  - Complicated.
- [Trello bug bounty: Payments informations are sent to the webhook when a team changes its visibility](https://hethical.io/trello-bug-bounty-payments-informations-are-sent-to-the-webhook-when-a-team-changes-its-visibility/) by Florian Courtial
  - A vulnerability about webhook which I don't understand.
- [Trello bug bounty: The websocket receives data when a public company creates a team visible board](https://hethical.io/trello-bug-bounty-the-websocket-receives-data-when-a-public-company-creates-a-team-visible-board/) by Florian Courtia
  - A vulnerability about websocket which I don't understand.
- [Mass Assignment, Response to Request Injection, Admin Escalation](https://seanmelia.wordpress.com/2017/06/01/privilege-escalation-in-a-django-application/) by Sean Melia
  - I don't understand, was this about guessing parameters?
- [Bypassing IDOR via Parameter pollution](http://blog.gaurangbhatnagar.com/2017/12/02/Hacking-a-dating-app.html) by Gaurang Bhatnagar
  - This writeup listed seven vulnerabilities found in a mobile dating app. This app was terrible.
- [Get as image function pulls any Insights/NRQL data from any New Relic account (IDOR)](https://jonbottarini.com/2018/10/09/get-as-image-function-pulls-any-insights-nrql-data-from-any-new-relic-account-idor/) by Jon Bottarini
  - This writeup was very specific about the product.

### Sensitive Information Exposure

- [Facebook: Unauthorized access to credit/prepaid card details (limited) of any user](https://pranavhivarekar.in/2017/02/11/facebooks-bug-unauthorized-access-to-credit-card-details-limited-of-any-user/) by PRANAV HIVAREKAR
  - The author exploited this by using GraphQL. This method is not applicable for me at this time.
- [Getting any Facebook User's Friend List and Partial Payment Card Details](https://www.josipfranjkovic.com/blog/facebook-friendlist-paymentcard-leak) by JOSIP FRANJKOVIĆ
  - The author exploited this by using GraphQL. This method is not applicable for me at this time.
- [Facebook Source Code Disclosure in ads API](https://www.amolbaikar.com/facebook-source-code-disclosure-in-ads-api/) by Amol Baikar
  - The author exploited this by using GraphQL. This method is not applicable for me at this time.
- [An interesting Google vulnerability that got me 3133.7 reward](http://www.sec-down.com/wordpress/?p=809) by zigoo
  - Complicated.
- [Exploiting Directory Traversal to View Customer Credit Card Information on Yahoo’s Small Business Platform](https://samcurry.net/exploiting-directory-traversal-on-a-yahoo-acquisition/) by samwcyo
  - The author managed to guesse how developer coding. Something about "Node.js".
- [Sensitive data exposure by requesting a resource with a different content type](https://medium.com/@yogendra_h1/sensitive-data-exposure-by-requesting-a-resource-with-a-different-content-type-27412a9d6e2f) by Yogendra Jaiswal
  - I didn't see what the author did (Atom? What's that?).
- [Twitter's OAuth Mistakes - $3k Bug Bounty](https://shkspr.mobi/blog/2018/12/twitter-bug-bounty/) [hackerone report](https://hackerone.com/reports/434763) by edent
  - I don't understand this writeup at this point.
- [Directory Listing To Sensitive Files Exposure](https://blog.hx01.me/2018/04/directory-listing-to-sensitive-files.html) by Hx01
  - Too easy?
- [Reading ASP secrets for $17,000](https://samcurry.net/reading-asp-secrets-for-17000/) by samwcyo

### Authentication Bypass

- [Hacking Facebook’s Legacy API, Part 1: Making Calls on Behalf of Any User](https://stephensclafani.com/2014/07/08/hacking-facebooks-legacy-api-part-1-making-calls-on-behalf-of-any-user/) by Stephen Sclafani
- [Hacking Facebook’s Legacy API, Part 2: Stealing User Sessions](https://stephensclafani.com/2014/07/29/hacking-facebooks-legacy-api-part-2-stealing-user-sessions/) by Stephen Sclafani
  - Awesome.
- [Bypass Admin approval, Mute Member and Posting Permissions for Only admins in Facebook groups](https://medium.com/bugbountywriteup/bypass-admin-approval-mute-member-and-posting-permissions-for-only-admins-in-facebook-groups-ef476cb3d524) by Sarmad Hassan
  - The author could make "Watch Party post" in another group that he was member in it by just changing `group_id` parameter.
  - Changing `group_id` also works even if the admin of victim group muted the attacker he still be able to make watch party video and bypass mute option.
  - The author used "Graph API".
- [Bypassing Firebase authorization to create custom goo.gl subdomains](https://blog.thomasorlita.cz/vulns/bypassing-firebase-authorization-to-create-custom-goo-gl-subdomains/) by ThomasOrlita
  - Since the support of `goo.gl` has already ended, the author have been looking for ways to shorten URLs using Google services. Some time ago he has found a bug that allowed him to shorten links using Google's official `g.co` shortener. This time he took a look at [Firebase Dynamic Links](https://firebase.google.com/docs/dynamic-links/).
  - A regular user can create custom subdomains on `app.goo.gl` via "Firebase Console". This should be possible to do only by Google.
  - Not that interesting.
- [YAHOO SMALL BUSINESS (LUMINATE) AND THE NOT-SO-SECRET KEYS](https://dos.sh/blog/2017/6/21/yahoo-small-business-luminate-and-the-not-so-secret-keys) by Tommy DeVoss
  - "Luminate Small Business" allows users to list local businesses, create websites (and host them on Yahoo servers), create stores / shops, and purchase various things such as domains etc.
  - After spending some time looking at the "free" portions of the sites, the author decided that it would be best if he purchased accounts to get access to more functionality to test.
  - Not much clear.
- [How I gained access to chef, docker, AWS, and MongoDB instances in a single request](https://samcurry.net/how-i-gained-access-to-chef-docker-aws-and-mongodb-instances-in-a-single-request/) by samwcyo
  - The author detailed the successful exploitation of a server sided request forgery vulnerability in Yahoo's small business platform.
  - The writeup maybe have some relationship with the previous one. Not much clear.
- [Decoding a .htpasswd to Earn a Payload of Money](https://blog.it-securityguard.com/bugbounty-decoding-a-%F0%9F%98%B1-00000-htpasswd-bounty/) by Patrik Fehrenbach
  - A private bug bounty program had a globally readable `.htpasswd` file. The author cracked the DES hash, got access to development and staging environments.
  - The author showed how to crack the DES.
- [From JS to another JS files lead to authentication bypass](https://blog.yappare.com/2017/06/from-js-to-another-js-files-lead-to.html) by yappare
  - This was found in a private bug bounty. The scope was limited to a few of features that available to the public. Based on the previous reported issues, seemed it was hard to find a new issue. It also mentioned in the bounty details that: "If you manage to get into Administration page, report immediately and do not pivot or further testing in `/admin`". Restricted.
  - However, there is an "administration page" which was restricted to unauthenticated and unauthorised users. Browsing to `/login` or `/admin` will redirect us to `https://bountysite.com/admin/dashboard?redirect=/`.
    - Look at the source page, nothing much useful.
  - The author started looking on the application's structure. It seems the JS files were located in few directories such as `/lib`, `/js`, `application` and etc.
    - He ran the Burpsuite and ran the "Intruder" to identify any accessible JS files in these directories. One of the accessible JS files was `/login.js`.
    - Accessing the JS file `https://bountysite.com/admin/dashboard/js/login.js` redirect him to the "administration page". But he had no permission to view it.
  - It seems weird why the page is loaded as an HTML while he browsed to a JS file. After playing around, he noticed that the actual reason that allowed him to get into this "administration page" was because the `login` word. As long the request after `/dashboard` contains a word with the string of `login` will allow him to get into this "administration page" without a right authorisation.
  - "Javascript analysis" wins.

- [Bypassing Google Email Domain Check to Deliver Spam Email on Google’s Behalf](http://web.archive.org/web/20161209085817/http://ngailong.com/bypassing-google-email-domain-check-to-deliver-spam-email-on-googles-behalf/) by Ron Chan
- [Bypassing Google’s authentication to access their Internal Admin panels](https://medium.com/bugbountywriteup/bypassing-googles-fix-to-access-their-internal-admin-panels-12acd3d821e3) by Vishnu Prasad P G
- [How I hacked Google’s bug tracking system itself for $15,600 in bounties](https://medium.freecodecamp.org/messing-with-the-google-buganizer-system-for-15-600-in-bounties-58f86cc9f9a5) by Alex Birsan
- [I bypassed "How I hacked Google’s bug tracking system itself for $15,600 in bounties." Here’s how](https://medium.freecodecamp.org/i-bypassed-how-i-hacked-googles-bug-tracking-system-itself-for-15-600-in-bounties-here-s-how-3355c8c63955) by Gopal Singh
- [Using a GitHub app to escalate to an organization owner for a $10,000 bounty](https://medium.com/@cachemoney/using-a-github-app-to-escalate-to-an-organization-owner-for-a-10-000-bounty-4ec307168631) by Tanner
- [Unauthorized Access to Unisphere Management Server Debugging Facility on https://bf1-uaddbcx-002.data.bf1.yahoo.com/Debug/](https://medium.com/@zk34911/yahoo-bug-bounty-unauthorized-access-to-unisphere-management-server-debugging-facility-on-448aeb6d0c94) by zk34911
- [Yahoo! Luminate Internal Privilege Escalation — Admin to Owner](https://medium.com/@rojanrijal/luminate-internal-privilege-escalation-admin-to-owner-2ca28e575985) by Rojan Rijal
- [Source Code Analysis in YSurvey — Luminate bug](https://medium.com/@rojanrijal/source-code-analysis-in-ysurvey-luminate-bug-c86dc29b70c4) by Rojan Rijal
- [Bypassing the Current Password Protection at PayPal TechSupport Portal](https://medium.com/@YoKoKho/bypassing-the-current-password-protection-at-techsupport-portal-b9005ee17e64) by YoKo Kho
- [How I hacked hundreds of companies through their helpdesk](https://medium.com/@intideceukelaire/how-i-hacked-hundreds-of-companies-through-their-helpdesk-b7680ddc2d4c) by Inti De Ceukelaire
- [How i hacked help desk of a Company](https://medium.com/@alirazzaq/how-i-hacked-help-desk-of-a-company-55dc22448446) by Ali Razzaq
- [How signing up for an account with an @company.com email can have unexpected results](https://medium.com/@zseano/how-signing-up-for-an-account-with-an-company-com-email-can-have-unexpected-results-7f1b700976f5) by Sean
- [Response To Request Injection (RTRI)](http://web.archive.org/web/20160907083447/https://www.bugbountyhq.com/front/latestnews/dWRWR0thQ2ZWOFN5cTE1cXQrSFZmUT09/) by ?
  - be honest, thanks to this article, I have found quite a few bugs because of using his method, respect to the author!
- [How re-signing up for an account lead to account takeover](https://medium.com/@zseano/how-re-signing-up-for-an-account-lead-to-account-takeover-3a63a628fd9f) by Sean
- [How I was able to compromise user account via HTTP Parameter Pollution(HPP)](https://medium.com/@logicbomb_1/bugbounty-compromising-user-account-how-i-was-able-to-compromise-user-account-via-http-4288068b901f) by Avinash Jain
- [Bypassing Captcha Like a Boss](https://medium.com/bugbountywriteup/bypassing-captcha-like-a-boss-d0edcc3a1c1) by Ak1T4
- [How I hijacked your account when you opened my cat picture](https://medium.com/intigriti/how-i-hijacked-your-account-when-you-opened-my-cat-picture-9a0a0acca9e8) by Matti Bijnens
- [How could I completely takeover any user’s account in an online classified ads company](https://medium.com/bugbountywriteup/bugbounty-i-dont-need-your-current-password-to-login-into-your-account-how-could-i-e51a945b083d) by Avinash Jain
- [How I could book cab using your wallet money in India’s largest auto transportation company](https://medium.com/bugbountywriteup/bugbounty-how-i-could-book-cab-using-your-wallet-money-in-indias-largest-auto-transportation-e0c4252ca1a3) by Avinash Jain
- [How I was able to Compromise any User Account via Reset Password Functionality](https://medium.com/bugbountywriteup/bugbounty-how-i-was-able-to-compromise-any-user-account-via-reset-password-functionality-a11bb5f863b3) by Avinash Jain
- [How I was able to hack any user account via password reset](https://medium.com/@BgxDoc/bugbounty-how-i-was-able-to-hack-any-user-account-via-password-reset-9009d84d94ff) by Bikash Gupta

- [How i was able to get admin panel on a private program](http://cybristerboy.blogspot.com/2018/05/how-i-was-able-to-get-admin-panel-on.html) by CybristerBoy
- [Password reset to full account takeover](https://medium.com/@hamzabet/password-reset-to-full-account-takeover-8a1e0a395987) by Hamza Bettache
- [User Account Takeover-I just need your email id to login into your shopping portal account](https://medium.com/@logicbomb_1/bugbounty-user-account-takeover-i-just-need-your-email-id-to-login-into-your-shopping-portal-7fd4fdd6dd56) by Avinash Jain
- [Authentication bypass in NodeJS application — a bug bounty story](https://medium.com/bugbountywriteup/authentication-bypass-in-nodejs-application-a-bug-bounty-story-d34960256402) by bl4de
- [Bypassing Authentication Using Javascript Debugger](https://mohitdabas.wordpress.com/2018/09/18/bypassing-authentication-using-javascript-debugger/) by mohitdabas
- [How I was Able To Bypass Email Verification](https://blog.securitybreached.org/2018/12/08/how-i-was-able-to-bypass-email-verification/) by Muzammil Kayani
- [How i was able to pwned application by Bypassing Cloudflare WAF](https://medium.com/bugbountywriteup/bypass-cloudflare-waf-to-pwned-application-2c9e4f862319) by Gujjuboy10x00
- [How we tookover shopify accounts with one single click](https://wesecureapp.com/blog/how-we-tookover-shopify-accounts-with-one-single-click/) by Akhil Reni

### Stealing Access Token

- [Stealing Facebook access_tokens Using CSRF in Device Login Flow](https://www.josipfranjkovic.com/blog/hacking-facebook-csrf-device-login-flow) by JOSIP FRANJKOVIĆ
  - I think the author used "Facebook Graph API".
- [Google - Vulnerability in Hangouts Chat: from open redirect to code execution](https://blog.bentkowski.info/2018/07/vulnerability-in-hangouts-chat-aka-how.html) by Michal Bentkowski
  - "Hangout Chat" is an answer to "Slack". It might be used both in browser (at `https://chat.google.com`, requires "GSuite account") and as a desktop or mobile application.
  - The author found an "open redirect" vulnerability in desktop app.
- [Steal Google Oauth in Microsoft](http://blog.intothesymmetry.com/2015/06/on-oauth-token-hijacks-for-fun-and.html) by Antonio Sanso
  - Complicated.
- [Holy redirect_uri Batman, Google tokens leak](http://blog.intothesymmetry.com/2016/05/holy-redirecturi-batman.html) by Antonio Sanso
  - There were some links between the previous writeup and this one. Complicated.
- [How I made LastPass give me all your passwords](https://labs.detectify.com/2016/07/27/how-i-made-lastpass-give-me-all-your-passwords/) by Mathias Karlsson
  - This vulnerability was in "LastPass browser extension".

### Business Logic Flaw

- [How I Could Steal Money from Instagram, Google and Microsoft](https://www.arneswinnen.net/2016/07/how-i-could-steal-money-from-instagram-google-and-microsoft/) by Arne Swinnen
  - Complicated.
- [Security Questions are not secure](https://labs.detectify.com/2017/12/20/security-questions-are-not-secure/) by Linus Särud
  - This is a security research paper.
- [The Unknown Hero-App Logic Bugs](https://medium.com/bug-bounty-hunting/application-logic-bugs-600245fb5bf0) by Circle Ninja
  - The author "Inspect Element" and enabled a button. I don't think this was a business logic flaw.
- [RECAPTCHA BYPASS VIA HTTP PARAMETER POLLUTION](https://andresriancho.com/recaptcha-bypass-via-http-parameter-pollution/) by andresriancho
  - Unusual.
- [How a simple readout of Peter Yaworski’s Web Hacking 101 got me into Microsoft Hall of fame](https://medium.com/bug-bounty-hunting/microsoft-hall-of-fame-by-reading-web-hacking-101-217d7838e3bf) by Circle Ninja
  - This was a HTTP parameter pollution vulnerability.

### HTTP Header Injection

- [CRLF injection on Twitter or why blacklists fail](https://blog.innerht.ml/twitter-crlf-injection/) by filedescriptor
  - CRLF injection attack usually occurs when there is an input being reflected in a header field of a HTTP response. If the output is not properly sanitized, attackers can inject arbitrary headers or contents into the response.
  - Twitter setup a page for ads haters to report ads vialations. In the page, there are a couple of inputs being reflected in `Set-Cookie`.
  - After a bit fiddling, the author discovered that non-printable control characters were not encoded which they should be.
    - However, this issue alone did not lead to big problems because two critical control characters (CR and LF) were sanitized.
    - "LR" was replaced with a space and "CR" would result in HTTP 400 ("Bad Request Error").
  - Complicated.
- [Twitter Overflow Trilogy in Twitter](https://blog.innerht.ml/overflow-trilogy/) by filedescriptor
  - Complicated.
- [Exploiting CRLF Injection can lands into a nice bounty](https://medium.com/bugbountywriteup/bugbounty-exploiting-crlf-injection-can-lands-into-a-nice-bounty-159525a9cb62) by Avinash Jain
  - An online food delivery company of India. In their home page, there are a couple of inputs being reflected into the HTTP headers.
  - After a bit fiddling, the author discovered that non-printable control characters were not encoded which they should be.
    - So he tried for CRLF and he tried to add `Location` header to see whether it was getting redirected.
    - Payload `/%0d%0aLacation:%20http://www.evilzone.org`, worked.
  - Fixed: a simple solution for CRLF injection is to sanitise the CRLF characters before passing into the header or to encode the data which will prevent the CRLF sequences entering the header.

### Subdomain Takeover

- [Hijacking tons of Instapage expired users Domains & Subdomains](http://www.geekboy.ninja/blog/hijacking-tons-of-instapage-expired-users-domains-subdomains/) by Geekboy
  - Nothing new.

### Local File Inclusion

- [Multiple Company LFI](http://panchocosil.blogspot.com/2017/05/one-cloud-based-local-file-inclusion.html) by panchocosil
  - An email from `bdev@em.facebookmail.com` got the author interested on the subdomain `em.facebookmail.com`.
  - The author didn't show how he found that LFI vulnerability.
- [How we got LFI in apache Drill (Recon like a boss)](https://medium.com/bugbountywriteup/how-we-got-lfi-in-apache-drill-recon-like-a-boss-6f739a79d87d) by Gujjuboy10x00
  - Exploit LFI by using syntax defined in Dill's docs. Complicated.

### Unrestricted File Upload

- [Arbitrary file upload in ubernihao.com](https://medium.com/@daksh_/arbitrary-file-upload-in-ubernihao-com-77ad40a4850a) by Daksh Patel
- [How i Hacked into a PayPal's Server - Unrestricted File Upload to Remote Code Execution](http://web.archive.org/web/20170721135642/http://blog.pentestbegins.com/2017/07/21/hacking-into-paypal-server-remote-code-execution-2017/) by Vikas Anil Sharma
- [RBookFresh Tricky File Upload Bypass to RCE](https://www.secgeek.net/bookfresh-vulnerability/) by secgeek
  - Complicated, maybe I can understand this method later.

### Brute Force

- [InstaBrute: Two Ways to Brute-force Instagram Account Credentials](https://www.arneswinnen.net/2016/05/instabrute-two-ways-to-brute-force-instagram-account-credentials/) by Arne Swinnen
  - Instagram contained two distinct vulnerabilities that allowed an attacker to brute-force passwords of user account. Combined with user enumeration, a weak password policy, no 2FA nor other mitigating security controls, this could have allowed an attacker to compromise many accounts without any user interaction.
  - Implementation bug in mobile authentication brute-force protection.
  - Credentials oracle in web registration endpoint.
  - Not applicable for me.
- [How I was able to enumerate Instagram Accounts who had enabled 2FA (Two Step Verification) for additional protection](https://medium.com/@zk34911/facebook-bug-bounty-how-i-was-able-to-enumerate-instagram-accounts-who-had-enabled-2fa-two-step-fddba9e9741c) by zk34911
  - "Instagram" only used to use text messaging code based 2FA unlike supporting a strong 2FA based authentication system such as "Authy". It only used to send a six digit code to a user's mobile number after logging in with the email and password to authorize the login attempt.
  - The author realized that if he changed the `username` to any ohter valid Instagram username in use, he could figure out if the following Instagram account has enabled 2FA for its additional protection by comparing the body of the HTTP responses (note, the author didn't bypass the 2FA).
  - The author was awarded a bounty by Facebook.

### Race Condition

- [Race conditions on Facebook, DigitalOcean and others (fixed)](http://josipfranjkovic.blogspot.com/2015/04/race-conditions-on-facebook.html) by Josip Franjković
- [Race Conditions on Web](https://www.josipfranjkovic.com/blog/race-conditions-on-web) by JOSIP FRANJKOVIĆ
- [Hacking Starbuck for unlimited money](https://sakurity.com/blog/2015/05/21/starbucks.html) by Egor Homakov
- [Manipulation of ETH balance](https://www.vicompany.nl/magazine/from-christmas-present-in-the-blockchain-to-massive-bug-bounty) by Jesse Lakerveld

### SQL Injection

- [Yahoo – Root Access SQL Injection – tw.yahoo.com](http://buer.haus/2015/01/15/yahoo-root-access-sql-injection-tw-yahoo-com/) by Brett Buerhaus
- [Yahoo SQL Injection to Remote Code Exection to Root Privilege](http://www.sec-down.com/wordpress/?p=494) by Ebrahim Hegazy
- [GitHub Enterprise SQL Injection](http://blog.orange.tw/2017/01/bug-bounty-github-enterprise-sql-injection.html) by Orange Tsai
- [Blind SQL Injection in er..I'm not sure what's the DBMS is](http://c0rni3sm.blogspot.com/2017/03/blind-sql-injection-in-erim-not-sure.html) by c0rni3sm
- [Anonymous SQL Execution in Oracle Advanced Support](https://blog.netspi.com/anonymous-sql-execution-oracle-advanced-support/) by Eric Gruber
- [Making a Blind SQL Injection a Little Less Blind](https://medium.com/@tomnomnom/making-a-blind-sql-injection-a-little-less-blind-428dcb614ba8) by TomNomNom
- [SQL Injection Vulnerability bootcamp.nutanix.com](https://blog.securitybreached.org/2018/09/08/sqli-bootcampnutanix-com-bug-bounty-poc/) by babayaga47
- [Authentication Bypass Using SQL Injection AutoTrader Webmail](https://blog.securitybreached.org/2018/09/10/sqli-login-bypass-autotraders/) by babayaga47
- [SQL injection with load file and into outfile](https://medium.com/bugbountywriteup/sql-injection-with-load-file-and-into-outfile-c62f7d92c4e2) by NoGe
- [Union Based Sql injection Write up ->A private Company Site](https://medium.com/@nuraalamdipu/union-based-sql-injection-write-up-a-private-company-site-273f89a49ed9) by Nur A Alam Dipu
-[A Five Minute SQL-I](https://medium.com/bugbountywriteup/a-five-minute-sql-i-16ab75b20fe4) by Ashish Jha
- [Bypassing Host Header to SQL injection to dumping Database — An unusual case of SQL injection](https://blog.usejournal.com/bugbounty-database-hacked-of-indias-popular-sports-company-bypassing-host-header-to-sql-7b9af997c610) by Avinash Jain
  - I can't understand this type vulnerability so far.

### Remote Code Execution

- [Facebaook Acquisition: Popping a shell on the Oculus developer portal](https://bitquark.co.uk/blog/2014/08/31/popping_a_shell_on_the_oculus_developer_portal) by Bitquark
- [How I Hacked Facebook, and Found Someone's Backdoor Script](http://devco.re/blog/2016/04/21/how-I-hacked-facebook-and-found-someones-backdoor-script-eng-ver/) by Orange Tsai
- [Remote Code Execution on a Facebook server](https://blog.scrt.ch/2018/08/24/remote-code-execution-on-a-facebook-server/) by Daniel Le Gall
- [GitHub Enterprise Remote Code Execution](https://www.exablue.de/blog/2017-03-15-github-enterprise-remote-code-execution.html) by iblue
- [How I Chained 4 vulnerabilities on GitHub Enterprise, From SSRF Execution Chain to RCE](http://blog.orange.tw/2017/07/how-i-chained-4-vulnerabilities-on.html) by Orange Tsai
- [Yahoo! Remote Command Execution Vulnerability](http://www.sec-down.com/wordpress/?p=87) by Ebrahim Hegazy
  - This started with a "Remote PHP Code Injection" vulnerability that later escalated to "Remote Command Execution".
  - `http://tw.user.mall.yahoo.com/rating/list?sid=$Vulnerability` (how did the author find out this?)
    - Checked the directories and files by `dir` using the SYSTEM function: `http://tw.user.mall.yahoo.com/rating/list?sid=${@print(system(“dir”))}`
    - A better view: `http://tw.user.mall.yahoo.com/rating/list?sid=${@print(system(“ls%20-la”))}`, it didn't work, it didn't accept any spaces in the URL.
  - The author was able to execute commands using `system($_POST[‘x2’])`.
- [Yahoo Remote Code Execution on cms.snacktv.de](https://seanmelia.files.wordpress.com/2016/02/yahoo-remote-code-execution-cms1.pdf) by Sean Melia
- [Command Injection in Yahoo Acquisition](http://samcurry.net/how-i-couldve-taken-over-the-production-server-of-a-yahoo-acquisition-through-command-injection/) by samwcyo
- [Remote Code Execution by struct2 Yahoo Server](https://medium.com/@th3g3nt3l/how-i-got-5500-from-yahoo-for-rce-92fffb7145e6) by Th3G3nt3lman
- [RCE on Yahoo Luminate](https://sites.google.com/securifyinc.com/secblogs/yahoo-luminate-rce) by Rojan Rijal
- [How I found 2.9 RCE at Yahoo! Bug Bounty program](https://medium.com/@kedrisec/how-i-found-2-9-rce-at-yahoo-bug-bounty-program-20ab50dbfac7) by Kedrisec
- [Airbnb – Ruby on Rails String Interpolation led to Remote Code Execution](https://buer.haus/2017/03/13/airbnb-ruby-on-rails-string-interpolation-led-to-remote-code-execution/) by Brett Buerhaus
- [How we broke PHP, hacked Pornhub and earned $20,000](https://www.evonide.com/how-we-broke-php-hacked-pornhub-and-earned-20000-dollar/) by Ruslan Habalov
  - *Alert*, God-like Write-up, make sure you know what is ROP before clicking, which I don't =(
- [How I hacked Pornhub for fun and profit - 10,000$](https://5haked.blogspot.sg/) by 5haked
- [PayPal Node.js code injection (RCE)](http://artsploit.blogspot.com/2016/08/pprce2.html) by Michael Stepankin
- [Telekom.de Remote Command Execution!](http://www.sec-down.com/wordpress/?p=581) by Ebrahim Hegazy
- [Magento Remote Code Execution Vulnerability!](http://www.sec-down.com/wordpress/?p=578) by Ebrahim Hegazy
- [Command Injection Vulnerability in Hostinger](http://elladodelnovato.blogspot.com/2017/02/command-injection-vulnerability-in.html) by Alberto Segura
- [$50k RCE in JetBrains IDE](http://blog.saynotolinux.com/blog/2016/08/15/jetbrains-ide-remote-code-execution-and-local-file-disclosure-vulnerability-analysis/) by Jordan Milne
- [Pentest: 0day in iTop 2.4.0 gave me Domain Admin Priviledges](https://httpsonly.blogspot.com/2018/04/pentest-0day-in-itop-240-gave-me-domain.html) by httpsonly
- [RCE due to ShowExceptions](https://sites.google.com/view/harshjaiswalblog/rce-due-to-showexceptions) by Harsh Jaiswal
- [How I Chained 4 Bugs(Features?) into RCE on Amazon Collaboration System](http://blog.orange.tw/2018/08/how-i-chained-4-bugs-features-into-rce-on-amazon.html) by Orange Tsai
- [No RCE? Then SSH to the box!](http://blog.jr0ch17.com/2018/No-RCE-then-SSH-to-the-box/) by Jasmin Landry
- [How I was able to bypass firewall to get RCE and then went from server shell to get root user account](https://medium.com/@logicbomb_1/bugbounty-how-i-was-able-to-bypass-firewall-to-get-rce-and-then-went-from-server-shell-to-get-783f71131b94) by Avinash Jain
- [Second bite on GitLab, and some interesting Ruby functions/features](https://blog.nyangawa.me/jekyll/update/2018/12/12/CVE-2018-18649-Gitlab-RCE.html) by Nyangawa
- [Pivoting from blind SSRF to RCE with HashiCorp Consul](http://www.kernelpicnic.net/2017/05/29/Pivoting-from-blind-SSRF-to-RCE-with-Hashicorp-Consul.html) by Peter Adkins
- [RCE in Hubspot with EL injection in HubL](https://www.betterhacker.com/2018/12/rce-in-hubspot-with-el-injection-in-hubl.html) by Aditya Gujar
- [Pwning JBoss Seam 2 like a boss](https://medium.com/@r0t1v/pwning-jboss-seam-2-like-a-boss-da5a43da6998) by Vitor"r0t"Oliveira
- [Server-Side Spreadsheet Injection – Formula Injection to Remote Code Execution](https://www.bishopfox.com/blog/2018/06/server-side-spreadsheet-injections/) by Jake Miller

####  Deserialization

- [Java Deserialization in manager.paypal.com](http://artsploit.blogspot.com/2016/01/paypal-rce.html) by Michael Stepankin
- [Java deserialization](https://seanmelia.wordpress.com/2016/07/22/exploiting-java-deserialization-via-jboss/) seanmelia

####  Image Tragick
  
- [FACEBOOK’S IMAGETRAGICK STORY](https://4lemon.ru/2017-01-17_facebook_imagetragick_remote_code_execution.html) by ANDREY LEONOV
- [bleed continues: 18 byte file, $14k bounty, for leaking private Yahoo! Mail images](https://scarybeastsecurity.blogspot.com/2017/05/bleed-continues-18-byte-file-14k-bounty.html) by Chris
- [bleed, more powerful: dumping Yahoo! authentication secrets with an out-of-bounds read](https://scarybeastsecurity.blogspot.com/2017/05/bleed-more-powerful-dumping-yahoo.html) by Chris
- [Exploiting ImageMagick to get RCE on Polyvore (Yahoo Acquisition)](http://nahamsec.com/exploiting-imagemagick-on-yahoo/) by Ben Sadeghipour
- [Trello bug bounty: Access server's files using ImageTragick](https://hethical.io/trello-bug-bounty-access-servers-files-using-imagetragick/) by Florian Courtial

### Miscellaneous

- [Web Application Penetration Testing Course](https://docs.google.com/document/d/101EsKlu41ICdeE7mEv189SS8wMtcdXfRtua0ClYjP1M/edit)
- [Smart Contract Vulnerabilities](http://www.dasp.co/)
- [Tutorials](https://securityidiots.com/) by Security Idiots
- [HACKING NODEJS AND MONGODB](https://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html) by websecurify
- [Mongo DB Injection again](https://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html) by websecrify
- [Jumping to The Hell With 10 Attempts to Bypass Devil's WAF](https://medium.com/bugbountywriteup/jumping-to-the-hell-with-10-attempts-to-bypass-devils-waf-4275bfe679dd) by Ak1T4
- [High Risk Vulnerabilities within the DoD - Exploiting Coldfusion, Dotnet Nuke, Oracle, and more](https://medium.com/@alyssa.o.herrera/high-risk-vulnerabilities-within-the-dod-from-coldfusion-dotnet-nuke-oracle-and-more-cc730f748c69) by Alyssa Herrera
- [A penetration tester’s guide to sub-domain enumeration](https://blog.appsecco.com/a-penetration-testers-guide-to-sub-domain-enumeration-7d842d5570f6) by Bharath
- [Escalating low severity bugs to high](https://www.noob.ninja/2018/07/escalating-low-severity-bugs-to-high.html) by Noob Ninja
- [How to Hack WebSockets and Socket.io](https://www.blackhillsinfosec.com/how-to-hack-websockets-and-socket-io/) by Ethan Robish
- [ZERO-DAY RCE VIA XXE & SSRF ON NETGEAR STORA, SEAGATE HOME, AND MEDION LIFECLOUD NAS](http://www.paulosyibelo.com/2018/11/zero-day-rce-via-xxe-ssrf-on-netgear.html) by Paulos Yibelo
- [Google bug bounty for security exploit that influences search results](http://www.tomanthony.co.uk/blog/google-xml-sitemap-auth-bypass-black-hat-seo-bug-bounty/) by Tom
- [WEB APPLICATION PENETRATION TESTING NOTES](https://techvomit.net/web-application-penetration-testing-notes/) by Tech Vomit
- [Bypass CSP by Abusing XSS Filter in Edge](https://medium.com/bugbountywriteup/bypass-csp-by-abusing-xss-filter-in-edge-43e9106a9754) by Xiaoyin Liu

### Exclusive Bugbounty Writeup Blog

- [How I earned 60K+ from private program](https://medium.com/@sivakrishnasamireddi/how-i-earned-60k-from-private-program-71bd51554490) by Siva Krishna Samireddi
- [Just another tale of severe bugs on a private program](https://medium.com/@sivakrishnasamireddi/just-another-tale-of-severe-bugs-on-a-private-program-405870b03532) by Siva Krishna Samireddi
- [XS-Searching Google’s bug tracker to find out vulnerable source code](https://medium.com/@luanherrera/xs-searching-googles-bug-tracker-to-find-out-vulnerable-source-code-50d8135b7549) by Luan Herrera
- [Bug Bounty: Fastmail](https://medium.com/bugbountywriteup/bug-bounty-fastmail-feeda67905f5) by hyde

### Interesting but Seems Not Applicable Now
- [RPO that lead to information leakage in Google](http://blog.innerht.ml/rpo-gadgets/) by filedescriptor
- [IE & Edge URL Parsing Problem](https://labs.detectify.com/2016/10/24/combining-host-header-injection-and-lax-host-parsing-serving-malicious-data/) - by detectify
- [xss in Google by IE Weird Behavior](http://blog.bentkowski.info/2015/04/xss-via-host-header-cse.html)
- [Internet Explorer Has a URL Parsing Problem](https://blog.innerht.ml/internet-explorer-has-a-url-problem/) by Jigsaw
- [XSS by Tossing Cookies in Microsoft and Twitter](http://blog.wesecureapp.com/xss-by-tossing-cookies/) by Akhil Reni
- [How I could Steal Your Google Bug Hunter Account with Two Clicks in IE](https://ngailong.wordpress.com/2017/08/07/how-i-could-steal-your-google-bug-hunter-account-with-two-clicks-in-ie/) by Ron Chan
