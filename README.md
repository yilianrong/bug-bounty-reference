# Bug Bounty Reference

A list of bug bounty write-up that is categorized by the bug nature, this is inspired by https://github.com/djadmin/awesome-bug-bounty

# Introduction

I have been reading for Bug Bounty write-ups for a few months, I found it extremely useful to read relevant write-up when I found a certain type of vulnerability that I have no idea how to exploit. Let say you found a RPO (Relativce Path Overwrite) in a website, but you have no idea how should you exploit that, then the perfect place to go would be [here](https://blog.innerht.ml/rpo-gadgets/). Or you have found your customer is using oauth mechanism but you have no idea how should we test it, the other perfect place to go would be [here](https://whitton.io/articles/obtaining-tokens-outlook-office-azure-account/)

My intention is to make a full and complete list of common vulnerability that are publicly disclosed bug bounty write-up, and let Bug Bounty Hunter to use this page as a reference when they want to gain some insight for a particular kind of vulnerability during Bug Hunting, feel free to submit pull request. Okay, enough for chit-chatting, let's get started. 


- [Cross-Site Scripting (XSS)](#cross-site-scripting-xss)
- [Cross-Site Request Forgery (CSRF)](#cross-site-request-forgery-csrf)
- [Cross-Site Script Inclusion (XSSI)](#cross-site-script-inclusion-xssi)
- [Server Side Request Forgery (SSRF)](#server-site-request-forgery-ssrf)
- [XML External Entity (XXE)](#xml-external-entify-xxe)
- [Insecure Direct Object Reference (IDOR)](#insecure-direct-object-reference-idor)
- [Sensitive Information Exposure](#sensitive-information-exposure)
- [Authentication Bypass](#authentication-bypass)
- [Stealing Access Token](#stealing-access-token)
- [Business Logic Flaw](#business-logic-flaw)
- [HTTP Header Injection](#http-header-injection)
- [Subdomain Takeover](#subdomain-takeover)
- [Local File Inclusion](#local-file-inclusion)
- [Unrestricted File Upload](#unrestricted-file-upload)
- [Brute Force](#brute-force)
- [Race Condition](#race-condition)
- [SQL Injection](#sql-injection)
- [Remote Code Execution](#remote-code-execution)
- [Miscellaneous](#miscellaneous)
- [Exclusive Bugbounty Writeup Blog](#exclusive-bugbounty-writeup-blog)
- [Interesting but Seems Not Applicable Now](#interesting-but-seems-not-applicable-now)


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

- [How I bypassed Facebook CSRF Protection](https://blog.darabi.me/2015/04/bypass-facebook-csrf.html) by Pouya Darabi
- [How I bypassed Facebook CSRF once again](https://blog.darabi.me/2016/05/how-i-bypassed-facebook-csrf-in-2016.html) by Pouya Darabi
- [Messenger.com CSRF that show you the steps when you check for CSRF](https://whitton.io/articles/messenger-site-wide-csrf/) by Jack Whitton
- [Facebookmarketingdevelopers.com: Proxies, CSRF Quandry and API Fun](https://philippeharewood.com/facebookmarketingdevelopers-com-proxies-csrf-quandry-and-api-fun/) by phwd
- [Facebook GraphQL CSRF](https://philippeharewood.com/facebook-graphql-csrf/) by phwd
- [Hacking Facebook accounts using CSRF in Oculus-Facebook integration](https://www.josipfranjkovic.com/blog/hacking-facebook-oculus-integration-csrf) by JOSIP FRANJKOVIĆ
- [Add Credit Card to Any Uber account Through eats.uber.com](http://www.indohack.com/2017/07/add-credit-card-to-any-uber-account.html) by Vijay Kumar
- [Paypal bug bounty: Updating the Paypal.me profile picture without consent (CSRF attack)](https://hethical.io/paypal-bug-bounty-updating-the-paypal-me-profile-picture-without-consent-csrf-attack/) by Florian Courtial
- [Hacking PayPal Accounts with one click (Patched)](http://yasserali.com/hacking-paypal-accounts-with-one-click/) by Yasser Ali
- [PayPal BBP - I could’ve deleted All SMC messages](https://blog.ayoubaitelmokhtar.com/2018/06/paypal-bbp-i-couldve-deleted-all-smc.html) by Ayoub AIT ELMOKHTAR
- [How i Hacked your Beats account ? Apple Bug Bounty](https://aadityapurani.com/2016/07/20/how-i-hacked-your-beats-account-apple-bug-bounty/) by Additya Purani
- [How I was able to delete anyone’s account in an Online Car Rental Company](https://medium.com/bugbountywriteup/bugbounty-how-i-was-able-to-delete-anyones-account-in-an-online-car-rental-company-8a4022cc611) by Avinash Jain

## Cross-Site Script Inclusion (XSSI)

- [OWASP XSSI](https://www.owasp.org/images/f/f3/Your_Script_in_My_Page_What_Could_Possibly_Go_Wrong_-_Sebastian_Lekies%2BBen_Stock.pdf) by Sebastian Lekies and Ben Stock
- [Backdoor of All Flickr API Calls by XSSI](https://ngailong.wordpress.com/2017/08/11/open-door-to-all-flickr-api-calls-by-xssi/) by Ron Chan
- [Yahoo — Two XSSi vulnerabilities chained to steal user information](https://medium.com/@0xHyde/yahoo-two-xssi-vulnerabilities-chained-to-steal-user-information-750-bounty-e9bc6a41a40a) by hyde

### Server Side Request Forgery (SSRF)

- [SSRF to query google internal server](https://www.rcesecurity.com/2017/03/ok-google-give-me-all-your-internal-dns-information/) by rcesecurity
- [Into the Borg – SSRF inside Google production network](https://opnsec.com/2018/07/into-the-borg-ssrf-inside-google-production-network/) by Enguerran Gillier
- [Yahoo! When Server Side Request Forgery combine with Cross Site Scripting](http://web.archive.org/web/20170218205059/http://ngailong.com/what-could-happen-when-server-side-request-forgery-combine-with-cross-site-scripting/) by Ron Chan
- [How i found an SSRF in Yahoo! Guesthouse (Recon Wins)](https://medium.com/@th3g3nt3l/how-i-found-an-ssrf-in-yahoo-guesthouse-recon-wins-8722672e41d4) by Th3G3nt3lman
- [Airbnb – Chaining Third-Party Open Redirect into Server-Side Request Forgery (SSRF) via LivePerson Chat](https://buer.haus/2017/03/09/airbnb-chaining-third-party-open-redirect-into-server-side-request-forgery-ssrf-via-liveperson-chat/) by Brett Buerhaus
- [SSRF tips from BugBountyHQ of Images - Open Graph Protocol is a good case for Blind SSRF / Extract of Meta Data](https://twitter.com/BugBountyHQ/status/868242771617792000) by BugBountyHQ
- [SSRF to LFI](https://seanmelia.wordpress.com/2015/12/23/various-server-side-request-forgery-issues/) by seanmelia
- [SSRF to pivot internal network](https://seanmelia.files.wordpress.com/2016/07/ssrf-to-pivot-internal-networks.pdf) by seanmelia
- [ESEA Server-Side Request Forgery and Querying AWS Meta Data](https://buer.haus/2016/04/18/esea-server-side-request-forgery-and-querying-aws-meta-data/) by Brett Buerhaus
- [Pivoting fromm Blind SSRF to RCE](http://www.kernelpicnic.net/2017/05/29/Pivoting-from-blind-SSRF-to-RCE-with-Hashicorp-Consul.html) by Peter Adkins
- [Plotly AWS EC2 Metadata Disclosure via SSRF and a Stored XSS via Presentation Link)](https://ysx.me.uk/a-pair-of-plotly-bugs-stored-xss-and-aws-metadata-ssrf/) by Yasin Soliman
- [Blog post: Cracking the Lens: Targeting HTTP’s Hidden Attack-Surface ](https://portswigger.net/blog/cracking-the-lens-targeting-https-hidden-attack-surface) by James Kettle
- [How I Found CVE-2018-8819: Out-of-Band (OOB) XXE in WebCTRL](https://www.coalfire.com/The-Coalfire-Blog/June-2018/How-I-Found-CVE-2018-8819-Out-of-Band-(OOB)-XXE?feed=blogs) by Darrell Damstedt
- [Server-Side Request Forgery (SSRF) Attacks - Part 1: The basics](https://medium.com/poka-techblog/server-side-request-forgery-ssrf-attacks-part-1-the-basics-a42ba5cc244a) by Maxime Leblanc
- [Server-Side Request Forgery (SSRF) Attacks — Part 2: Fun with IPv4 addresses](https://medium.com/poka-techblog/server-side-request-forgery-ssrf-attacks-part-2-fun-with-ipv4-addresses-eb51971e476d) by Maxime Leblanc
- [Server-Side Request Forgery (SSRF) — Part 3: Other advanced techniques](https://medium.com/poka-techblog/server-side-request-forgery-ssrf-part-3-other-advanced-techniques-3f48cbcad27e) by Maxime Leblanc
- [SSRF bible. Cheatsheet](https://docs.google.com/document/d/1v1TkWZtrhzRLy0bYXBcdLUedXGb9njTNIJXa3u9akHM/mobilebasic) by d0znpp
- [Bypassing SSRF](http://www.infosec-research.com/bypassing-ssrf-bugbounty-tip/) by infosec
- [SSRF on DigitalOcean site](http://www.infosec-research.com/ssrf-on-digitalocean-site-bugbounty-tip/) by infosec
- [Exploiting a Single Parameter](https://medium.com/@hisham.mir/exploiting-a-single-parameter-6f4ba2acf523) by Hisham Mir
- [Piercing the Veil: Server Side Request Forgery to NIPRNet access](https://medium.com/bugbountywriteup/piercing-the-veil-server-side-request-forgery-to-niprnet-access-c358fd5e249a) by Alyssa Herrera
- [How i converted SSRF TO XSS in jira](https://medium.com/@D0rkerDevil/how-i-convert-ssrf-to-xss-in-a-ssrf-vulnerable-jira-e9f37ad5b158) by Ashish Kunwar
- [How I found XSS via SSRF vulnerability](https://medium.com/@adeshkolte/how-i-found-xss-via-ssrf-vulnerability-adesh-kolte-873b30a6b89f) by Adesh Kolte
- [GETTING READ ACCESS ON EDMODO PRODUCTION SERVER BY EXPLOITING SSRF](https://www.shawarkhan.com/2018/05/getting-read-access-on-edmodo.html) by SHAWAR KHAN
- [AWS takeover through SSRF in JavaScript](http://10degres.net/aws-takeover-ssrf-javascript/) by Gwen

### XML External Entity (XXE)

- [XML Entity Cheatsheet](https://www.silentrobots.com/blog/2015/12/14/xe-cheatsheet-update/) by silentrobots
- [How we got read access on Google’s production servers](https://blog.detectify.com/2014/04/11/how-we-got-read-access-on-googles-production-servers/) by  detectify
- [Blind OOB XXE At UBER 26+ Domains Hacked](http://nerdint.blogspot.hk/2016/08/blind-oob-xxe-at-uber-26-domains-hacked.html) by Raghav Bisht
- [0day in Code42 - XXE in uber.com to read local files](https://httpsonly.blogspot.com/2017/01/0day-writeup-xxe-in-ubercom.html) by httpsonly
- [Out of Band XML External Entity Injection via SAML SSO](https://seanmelia.files.wordpress.com/2016/01/out-of-band-xml-external-entity-injection-via-saml-redacted.pdf) by seanmelia
- [XXE by SVG in Lithium Community Platform](http://esoln.net/Research/2017/03/30/xxe-in-lithium-community-platform/) by Vibhuti Nath
- [Gainning Filesystem Access Via Blind OOB XXE](https://hawkinsecurity.com/2018/03/24/gaining-filesystem-access-via-blind-oob-xxe/) by tghawkins
- [Exploiting XXE with local DTD files](https://mohemiv.com/all/exploiting-xxe-with-local-dtd-files/) by Arseniy Sharoglazov
- [From blind XXE to root-level file read access](https://www.honoki.net/2018/12/from-blind-xxe-to-root-level-file-read-access/) by Honoki
- [Exploitation: XML External Entity (XXE) Injection](https://depthsecurity.com/blog/exploitation-xml-external-entity-xxe-injection) by Faisal Tameesh

### Insecure Direct Object Reference (IDOR)

- [Disclose Private Video Thumbnail from Facebook WorkPlace](https://medium.com/bugbountywriteup/disclose-private-video-thumbnail-from-facebook-workplace-52b6ec4d73b7) by Sarmad Hassan
- [View Insights for Any Facebook Marketplace Product](https://wongmjane.com/post/view-insights-for-any-fb-marketplace-product/) by Jane Manchun Wong
- [Dox Facebook Employees Behind “Did You Know” Questions](https://wongmjane.com/post/reveal-fb-employee-behind-funfact/) by Jane Manchun Wong
- [Disclose Facebook Internal Server Information With A Strange Poll](https://wongmjane.com/post/disclose-fb-intern-server-info-with-a-strange-poll/) by Jane Manchun Wong
  - In the previous three writeups the author used `GraphAPI` to extract sensitive information.
- [Add description to Instagram Posts on behalf of other users - 6500$](https://medium.com/bugbountywriteup/add-description-to-instagram-posts-on-behalf-of-other-users-6500-7d55b4a24c5a) by Sarmad Hassan
- [How I was able to delete any image in Facebook community question forum](https://medium.com/@JubaBaghdad/how-i-was-able-to-delete-any-image-in-facebook-community-question-forum-a03ea516e327) by Sarmad Hassan
- [Facebook: Creating Test Conversion using any App](https://medium.com/bugbountywriteup/creating-test-conversion-using-any-app-8b32ee0a735) by Joshua Regio
- [Vulnerability in Youtube allowed moving comments from any video to another](https://www.secgeek.net/youtube-vulnerability/) by secgeek
  - The author wanted to think a little bit outside the box and find something in Youtube that not many bug hunters have tested, so he has decided to test the feature of "reviewing comments". Usually, the comments get posted immediately to the uploaded videos, but the author of the channel can control this by changing the settings to hold the comments for review before it gets posted. The author thought that not many researchers have tested that feature since it is not the default option.
  - When you approved the a comment on your video, a request containing `comment_id` and `video_id` (in the "POST" parameters) was generated. If you changed the `video_id` to any other video id, you would get an error. Yet, if you kept the `video_id` untouched and changed only the `comment_id` to any other comment id on any Youtube video, the request would get accepted and that comment would be copied and appear on you video.
  - The original comment from the original video didn't get removed, and the author of the commnent didn't get nonified that his comment is copied onto another video.
- [Microsoft-careers.com Remote Password Reset](http://yasserali.com/microsoft-careers-com-remote-password-reset/) by Yaaser Ali
- [One Vulnerability allowed deleting comments of any user in all Yahoo sites](https://www.secgeek.net/yahoo-comments-vulnerability/) by secgeek
- [Airbnb – Web to App Phone Notification IDOR to view Everyone’s Airbnb Messages](https://buer.haus/2017/03/31/airbnb-web-to-app-phone-notification-idor-to-view-everyones-airbnb-messages/) by Brett Buerhaus
- [Twitter Vulnerability Could Credit Cards from Any Twitter Account](https://www.secgeek.net/twitter-vulnerability/) by secgeek
- [How I took control of your Twitter account (tweeting, viewing/deleting photos and other media)](http://www.anandpraka.sh/2017/05/how-i-took-control-of-your-twitter.html) by Anand Prakash
- [UnAuth Access to Twitter Private Tweets and messages Media Content Access](http://www.indohack.com/2017/07/unauth-access-to-twitter-private-tweets.html) by Vijay Kumar
- [How I could change your eBay password](http://yasserali.com/how-i-could-change-your-ebay-password/) by Yaaser Ali
- [Full account Takeover via reset password function](https://medium.com/@khaled.hassan/full-account-takeover-via-reset-password-function-8b6ef15f346f) by Khaled Hassan
- [How I could have hacked 62.5 million Zomato Users](http://www.anandpraka.sh/2015/06/how-i-hacked-zomatocom-to-see-data-of.html) by Anand Prakash
- [Trello bug bounty: Payments informations are sent to the webhook when a team changes its visibility](https://hethical.io/trello-bug-bounty-payments-informations-are-sent-to-the-webhook-when-a-team-changes-its-visibility/) by Florian Courtial
- [Trello bug bounty: The websocket receives data when a public company creates a team visible board](https://hethical.io/trello-bug-bounty-the-websocket-receives-data-when-a-public-company-creates-a-team-visible-board/) by Florian Courtia
- [How I got access to millions of -redacted- accounts](https://bitquark.co.uk/blog/2016/02/09/how_i_got_access_to_millions_of_redacted_accounts) by Bitquark
- [Mass Assignment, Response to Request Injection, Admin Escalation](https://seanmelia.wordpress.com/2017/06/01/privilege-escalation-in-a-django-application/) by sean
- [IDOR While Connecting Social Account in Hackster.io](https://medium.com/@arbazhussain/idor-while-connecting-social-account-in-hackster-io-2296b316b7a7) by Arbaz Hussain
- [How I could have hacked 62.5 million Zomato Users](https://medium.com/appsecure/responsible-disclosure-how-i-could-have-hacked-62-5-million-zomato-users-f14e2f8595ee) by Anand Prakash
- [Hacking a Dating App for Fun and Profit](http://blog.gaurangbhatnagar.com/2017/12/02/Hacking-a-dating-app.html) by Gaurang Bhatnagar
- [Hunting Insecure Direct Object Reference Vulnerabilities for Fun and Profit (PART-1)](https://codeburst.io/hunting-insecure-direct-object-reference-vulnerabilities-for-fun-and-profit-part-1-f338c6a52782) by Mohammed Abdul Raheem
- [Hunting Insecure Direct Object Reference Vulnerabilities for Fun and Profit (PART 2)](https://codeburst.io/hunting-insecure-direct-object-reference-vulnerabilities-for-fun-and-profit-part-2-af832d1c0bb6) by Mohammed Abdul Raheem
- [How I Get the Name of the Hotel (and other Data) that you ever Stay](https://medium.com/@YoKoKho/idor-at-private-bug-bounty-program-that-could-leads-to-personal-data-leaks-d2536d026bf5) by YoKo Kho
- [Ribose — IDOR with Simple CSRF Bypass — Unrestricted Changes and Deletion to other Photo Profile](https://medium.com/@YoKoKho/ribose-idor-with-simple-csrf-bypass-unrestricted-changes-and-deletion-to-other-photo-profile-e4393305274e) by YoKo Kho
- [How I hacked 23.900.000 tumblr domains at once](https://medium.com/bugbountywriteup/how-i-hack-23-900-000-tumblr-domains-at-once-341edad6e7cc) by Ak1T4
- [IDOR User Account Takeover By Connecting My Facebook Account with victims Account](https://blog.securitybreached.org/2018/09/16/idor-account-takeover-using-facebook/) by babayaga47
- [Paytm Customer Information is at risk — India’s largest digital wallet company](https://medium.com/@logicbomb_1/bugbounty-paytm-customer-information-is-at-risk-indias-largest-digital-wallet-company-6f7116d4b2d5) by Avinash Jain
- [How Naaptol (India’s popular home shopping company) Kept their Millions of User Data at Risk](https://medium.com/@logicbomb_1/bugbounty-how-naaptol-indias-popular-home-shopping-company-kept-their-millions-of-user-data-e414cd4151c) by Avinash Jain
- [Abusing internal API to achieve IDOR in New Relic](https://www.jonbottarini.com/2018/01/02/abusing-internal-api-to-achieve-idor-in-new-relic/) by Jon Bottarini
- [Get as image function pulls any Insights/NRQL data from any New Relic account (IDOR)](https://jonbottarini.com/2018/10/09/get-as-image-function-pulls-any-insights-nrql-data-from-any-new-relic-account-idor/) by Jon Bottarini
- [How-To: Find IDOR (Insecure Direct Object Reference) Vulnerabilities for large bounty rewards](https://www.bugcrowd.com/how-to-find-idor-insecure-direct-object-reference-vulnerabilities-for-large-bounty-rewards/) by Sam Houston
- [Rewarded by securing vulnerabilities in Bookmyshow (India’s largest online movie & event booking portal)](https://medium.com/@logicbomb_1/bugbounty-rewarded-by-securing-vulnerabilities-in-bookmyshow-indias-largest-online-movie-bb81dba9b82) by Avinash Jain

### Sensitive Information Exposure

- [FB users birth year disclosed via FB Timeline profile source code “data attribute”](https://medium.com/@rajsek/curiosity-and-passion-to-your-profession-might-lead-to-make-your-dream-come-true-7d9be3c6029a) by Raja Sekar Durairaj
- [FB user birth year Disclosure via “IDOR in m.facebook.com”](https://medium.com/@rajsek/my-2nd-facebook-bounty-poc-fb-data-of-birth-disclosure-d02e1bec50) by Raja Sekar Durairaj
- [DOB disclosed using “Facebook Graph API Reverse Engineering”](https://medium.com/@rajsek/my-3rd-facebook-bounty-hat-trick-chennai-tcs-er-name-listed-in-facebook-hall-of-fame-47f57f2a4f71#.9gbtbv42q) by Raja Sekar Durairaj
- [Abusing Facebook Graph Search using GraphQL](https://philippeharewood.com/abusing-facebook-graph-search/) by phwd
- [Facebook's Bug - Fooling Graph Search to Bypass Privacy Restrictions & Extract Private Information](https://pranavhivarekar.in/2016/02/20/facebooks-bug-fooling-graph-search-to-bypass-privacy-restrictions/) by PRANAV HIVAREKAR
- [Facebook: Unauthorized access to credit/prepaid card details (limited) of any user](https://pranavhivarekar.in/2017/02/11/facebooks-bug-unauthorized-access-to-credit-card-details-limited-of-any-user/) by PRANAV HIVAREKAR
- [Getting any Facebook User's Friend List and Partial Payment Card Details](https://www.josipfranjkovic.com/blog/facebook-friendlist-paymentcard-leak) by JOSIP FRANJKOVIĆ
- [Responsible disclosure: retrieving a user's private Facebook friends](https://rpadovani.com/facebook-responsible-disclosure) by Riccardo Padovani
- [FACEBOOK BUG BOUNTY: "GETTING ACCESS TO PROMPT DEBUG DIALOG AND SERIALIZED TOOL ON MAIN WEBSITE FACEBOOK.COM"](http://omespino.com/facebook-bug-bounty-getting-access-to-prompt-debug-dialog-and-serialized-tool-on-main-website-facebook-com/) by OMESPINO
- [Facebook Source Code Disclosure in ads API](https://www.amolbaikar.com/facebook-source-code-disclosure-in-ads-api/) by Amol Baikar
- [Facebook BugBounty — Disclosing page members](https://medium.com/@tnirmalz/facebook-bugbounty-disclosing-page-members-1178595cc520) by Nirmal Thapa
- [An interesting Google vulnerability that got me 3133.7 reward](http://www.sec-down.com/wordpress/?p=809) by zigoo
- [Exploiting Directory Traversal to View Customer Credit Card Information on Yahoo’s Small Business Platform](https://samcurry.net/exploiting-directory-traversal-on-a-yahoo-acquisition/) by samwcyo
- [Chaining Bugs (an XSS and a CORS misconfiguration) to Steal Yahoo Contacts](http://web.archive.org/web/20180112014611/https://www.sxcurity.pro/2018/01/11/chaining-yahoo-bugs/) by sxcurity
- [How I was able to list some internal information from PayPal](https://medium.com/@adrien_jeanneau/how-i-was-able-to-list-some-internal-information-from-paypal-bugbounty-ca8d217a397c) by Adrien
- [Sensitive data exposure by requesting a resource with a different content type](https://medium.com/@yogendra_h1/sensitive-data-exposure-by-requesting-a-resource-with-a-different-content-type-27412a9d6e2f) by Yogendra Jaiswal
- [How I used a simple Google query to mine passwords from dozens of public Trello boards](https://medium.freecodecamp.org/discovering-the-hidden-mine-of-credentials-and-sensitive-information-8e5ccfef2724) by Kushagra Pathak
- [Find Leaked Sensitive Data](https://sites.google.com/securifyinc.com/rojanrijal/finding-leaked-sensitive-data) by Rojan Rijal
- [Misconfigured JSON endpoint on ads.twitter.com lead to Access control issue and Information Disclosure of role privileged users](https://medium.com/@zk34911/twitter-bug-bounty-misconfigured-json-endpoint-on-ads-twitter-com-2771ec83a82) by zk34911
- [Twitter's OAuth Mistakes - $3k Bug Bounty](https://shkspr.mobi/blog/2018/12/twitter-bug-bounty/) [hackerone report](https://hackerone.com/reports/434763) by edent
- [How I was able to read chat of users in an Indian Online travel portal](https://medium.com/bugbountywriteup/bugbounty-how-i-was-able-to-read-chat-of-users-in-an-online-travel-portal-c55a1787f999) by Avinash Jain
- [How I was able to download the Source Code of India’s Largest Telecom Service Provider including dozens of more popular websites](https://medium.com/@logicbomb_1/bugbounty-how-i-was-able-to-download-the-source-code-of-indias-largest-telecom-service-52cf5c5640a1) by Avinash Jain
- [How I could download the source code of an Indian e-commerce website](https://medium.com/bugbountywriteup/how-i-could-download-the-source-code-of-an-indian-e-commerce-website-30cb8310b6e4) by Minali Arora
- [AWS S3 added to my "Bucket" list](https://medium.com/bugbountywriteup/bugbounty-aws-s3-added-to-my-bucket-list-f68dd7d0d1ce) by Avinash Jain
- [Directory Listing To Sensitive Files Exposure](https://blog.hx01.me/2018/04/directory-listing-to-sensitive-files.html) by Hx01
- [From an error message to DB disclosure](https://medium.com/@YumiSec/from-an-error-message-to-db-diclosure-1af879c74474) by Yumi
- [Reading ASP secrets for $17,000](https://samcurry.net/reading-asp-secrets-for-17000/) by samwcyo

### Authentication Bypass

- [Taking over Facebook Accounts using Free Basics Partner Portal](https://www.josipfranjkovic.com/blog/facebook-partners-portal-account-takeover) by JOSIP FRANJKOVIĆ
- [Hacking Facebook’s Legacy API, Part 1: Making Calls on Behalf of Any User](https://stephensclafani.com/2014/07/08/hacking-facebooks-legacy-api-part-1-making-calls-on-behalf-of-any-user/) by Stephen Sclafani
- [Hacking Facebook’s Legacy API, Part 2: Stealing User Sessions](https://stephensclafani.com/2014/07/29/hacking-facebooks-legacy-api-part-2-stealing-user-sessions/) by Stephen Sclafani
- [Critical Issue Opened Private Chats of Facebook Messenger Users Up to Attackers](https://www.cynet.com/blog-facebook-originull/) by cynet
- [How I hacked Tinder accounts using Facebook’s Account Kit](https://medium.freecodecamp.org/hacking-tinder-accounts-using-facebook-accountkit-d5cc813340d1) by Anand Prakash
- [How I Was Able to Takeover Facebook Account](https://blog.securitybreached.org/2017/12/10/how-i-was-able-to-takeover-facebook-account-bug-bounty-poc/) by Ameer Hamza
- [Bypass Admin approval, Mute Member and Posting Permissions for Only admins in Facebook groups](https://medium.com/bugbountywriteup/bypass-admin-approval-mute-member-and-posting-permissions-for-only-admins-in-facebook-groups-ef476cb3d524) by Sarmad Hassan
- [Facebook Bug Bounty! {Permission Bug}](https://medium.com/@alicanact60/facebook-bug-bounty-permission-bug-19c9358d2297) by alicanact60
- [Add comment on a private Oculus Developer bug report](https://medium.com/bugbountywriteup/add-comment-on-a-private-oculus-developer-bug-report-93f35bc80b2c) by Sarmad Hassan
- [Instagram Multi-factor authentication Bypass](https://medium.com/@vishnu0002/instagram-multi-factor-authentication-bypass-924d963325a1) by vishnuraj
- [How I was able to generate Access Tokens for any Facebook user](https://medium.com/bugbountywriteup/how-i-was-able-to-generate-access-tokens-for-any-facebook-user-6b84392d0342) by Samm0uda
- [Use XSS and Bug Chain to Bypass Google Account Recovery Restriction](https://sites.google.com/site/bughunteruniversity/best-reports/account-recovery-xss) by Ramzes
- [Bypassing Google Authentication on Periscope's Administration Panel](https://whitton.io/articles/bypassing-google-authentication-on-periscopes-admin-panel/) By Jack Whitton
- [Bypassing Google Email Domain Check to Deliver Spam Email on Google’s Behalf](http://web.archive.org/web/20161209085817/http://ngailong.com/bypassing-google-email-domain-check-to-deliver-spam-email-on-googles-behalf/) by Ron Chan
- [I got emails - G Suite Vulnerability](http://blog.pentestnepal.tech/post/156707088037/i-got-emails-g-suite-vulnerability) by uranium238
- [This domain is my domain - G Suite A record vulnerability](http://blog.pentestnepal.tech/post/156959105292/this-domain-is-my-domain-g-suite-a-record) by uranium238
- [Bypassing Google’s authentication to access their Internal Admin panels](https://medium.com/bugbountywriteup/bypassing-googles-fix-to-access-their-internal-admin-panels-12acd3d821e3) by Vishnu Prasad P G
- [How I hacked Google’s bug tracking system itself for $15,600 in bounties](https://medium.freecodecamp.org/messing-with-the-google-buganizer-system-for-15-600-in-bounties-58f86cc9f9a5) by Alex Birsan
- [I bypassed "How I hacked Google’s bug tracking system itself for $15,600 in bounties." Here’s how](https://medium.freecodecamp.org/i-bypassed-how-i-hacked-googles-bug-tracking-system-itself-for-15-600-in-bounties-here-s-how-3355c8c63955) by Gopal Singh
- [Bypassing Firebase authorization to create custom goo.gl subdomains](https://blog.thomasorlita.cz/vulns/bypassing-firebase-authorization-to-create-custom-goo-gl-subdomains/) by ThomasOrlita
- [How I could have stolen your photos from Google - my first 3 bug bounty writeups](https://blog.avatao.com/How-I-could-steal-your-photos-from-Google/) by Gergő Turcsányi
- [Office365 Auth Bypass - The road to hell is paved with SAML Assertions](http://www.economyofmechanism.com/office365-authbypass.html) by Yiannis Kakavas
- [Github SAML - The road to your codebase is paved with forged assertions](http://www.economyofmechanism.com/github-saml.html) by Yiannis Kakavas
- [Using a GitHub app to escalate to an organization owner for a $10,000 bounty](https://medium.com/@cachemoney/using-a-github-app-to-escalate-to-an-organization-owner-for-a-10-000-bounty-4ec307168631) by Tanner
- [Unauthorized Access to Unisphere Management Server Debugging Facility on https://bf1-uaddbcx-002.data.bf1.yahoo.com/Debug/](https://medium.com/@zk34911/yahoo-bug-bounty-unauthorized-access-to-unisphere-management-server-debugging-facility-on-448aeb6d0c94) by zk34911
- [Yahoo! Luminate Internal Privilege Escalation — Admin to Owner](https://medium.com/@rojanrijal/luminate-internal-privilege-escalation-admin-to-owner-2ca28e575985) by Rojan Rijal
- [Source Code Analysis in YSurvey — Luminate bug](https://medium.com/@rojanrijal/source-code-analysis-in-ysurvey-luminate-bug-c86dc29b70c4) by Rojan Rijal
- [Authentication bypass on Uber’s Single Sign-On via subdomain takeover](https://www.arneswinnen.net/2017/06/authentication-bypass-on-ubers-sso-via-subdomain-takeover/) by Arne Swinnen
- [Uber Bug Bounty: Gaining Access To An Internal Chat System](https://mishresec.wordpress.com/2017/10/13/uber-bug-bounty-gaining-access-to-an-internal-chat-system/) by mishre
- [Twitter's Vine Source code dump - $10080](https://avicoder.me/2016/07/22/Twitter-Vine-Source-code-dump/) by avicoder
- [How I gained access to chef, docker, AWS, and MongoDB instances in a single request](https://samcurry.net/how-i-gained-access-to-chef-docker-aws-and-mongodb-instances-in-a-single-request/) by samwcyo
- [2FA PayPal Bypass](https://henryhoggard.co.uk/blog/Paypal-2FA-Bypass) by henryhoggard
- [Bypassing the Current Password Protection at PayPal TechSupport Portal](https://medium.com/@YoKoKho/bypassing-the-current-password-protection-at-techsupport-portal-b9005ee17e64) by YoKo Kho
- [Decoding a .htpasswd to Earn a Payload of Money](https://blog.it-securityguard.com/bugbounty-decoding-a-%F0%9F%98%B1-00000-htpasswd-bounty/) by Patrik Fehrenbach
- [Slack SAML authentication bypass](http://blog.intothesymmetry.com/2017/10/slack-saml-authentication-bypass.html) by Antonio Sanso
- [From JS to another JS files lead to authentication bypass](http://c0rni3sm.blogspot.com/2017/06/from-js-to-another-js-files-lead-to.html) by c0rni3sm
- [Accidentally typo to bypass administration access](http://c0rni3sm.blogspot.com/2017/08/accidentally-typo-to-bypass.html) by c0rni3sm
- [How I hacked hundreds of companies through their helpdesk](https://medium.com/@intideceukelaire/how-i-hacked-hundreds-of-companies-through-their-helpdesk-b7680ddc2d4c) by Inti De Ceukelaire
- [How i hacked help desk of a Company](https://medium.com/@alirazzaq/how-i-hacked-help-desk-of-a-company-55dc22448446) by Ali Razzaq
- [How signing up for an account with an @company.com email can have unexpected results](https://medium.com/@zseano/how-signing-up-for-an-account-with-an-company-com-email-can-have-unexpected-results-7f1b700976f5) by Sean
- [GraphQL abuse: Bypass account level permissions through parameter smuggling](https://labs.detectify.com/2018/03/14/graphql-abuse/) by Jon Bottarini
- [Response To Request Injection (RTRI)](http://web.archive.org/web/20160907083447/https://www.bugbountyhq.com/front/latestnews/dWRWR0thQ2ZWOFN5cTE1cXQrSFZmUT09/) by ?
  - be honest, thanks to this article, I have found quite a few bugs because of using his method, respect to the author!
- [Attacking SSO: Common SAML Vulnerabilities and Ways to Find Them](https://blog.netspi.com/attacking-sso-common-saml-vulnerabilities-ways-find/) by Jem Jensen
- [Bypassing SAML 2.0 SSO with XML Signature Attacks](https://research.aurainfosec.io/bypassing-saml20-SSO/) by Tim Goddard
- [How re-signing up for an account lead to account takeover](https://medium.com/@zseano/how-re-signing-up-for-an-account-lead-to-account-takeover-3a63a628fd9f) by Sean
- [How I was able to compromise user account via HTTP Parameter Pollution(HPP)](https://medium.com/@logicbomb_1/bugbounty-compromising-user-account-how-i-was-able-to-compromise-user-account-via-http-4288068b901f) by Avinash Jain
- [How to Detect HTTP Parameter Pollution Attacks](https://www.acunetix.com/blog/whitepaper-http-parameter-pollution/) by ?
- [Bypassing Captcha Like a Boss](https://medium.com/bugbountywriteup/bypassing-captcha-like-a-boss-d0edcc3a1c1) by Ak1T4
- [Chaining Multiple Vulnerabilities to Gain Admin Access](https://nahamsec.com/chaining-multiple-vulnerabilities-to-gain-admin-access/) by NahamSec
- [ORACLE WEBLOGIC - MULTIPLE SAML VULNERABILITIES (CVE-2018-2998/CVE-2018-2933)](https://pulsesecurity.co.nz/advisories/WebLogic-SAML-Vulnerabilities) by Denis Andzakovic
- [Bypassing and exploiting Bucket Upload Policies and Signed URLs](https://labs.detectify.com/2018/08/02/bypassing-exploiting-bucket-upload-policies-signed-urls/) by Frans Rosén
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

- [Facebook Access Token Stolen](https://whitton.io/articles/stealing-facebook-access-tokens-with-a-double-submit/) by Jack Whitton
- [Stealing Facebook Messenger Login Nonces worth 15k](https://stephensclafani.com/2017/03/21/stealing-messenger-com-login-nonces/) by Stephen Sclafani
- [Stealing Facebook access_tokens Using CSRF in Device Login Flow](https://www.josipfranjkovic.com/blog/hacking-facebook-csrf-device-login-flow) by JOSIP FRANJKOVIĆ
- [Steal Oculus Nonce and Oauth Flow Bypass](https://medium.com/@lokeshdlk77/bypass-oauth-nonce-and-steal-oculus-response-code-faa9cc8d0d37)
- [A tale about appengine.google.com authentication and life](https://proximasec.blogspot.com/2017/02/a-tale-about-appengines-authentication.html) by Andrey's Ramblings
- [Vulnerability in Hangouts Chat a.k.a. how Electron makes open redirect great again](https://blog.bentkowski.info/2018/07/vulnerability-in-hangouts-chat-aka-how.html) by Michal Bentkowski
- [Steal Google Oauth in Microsoft](http://blog.intothesymmetry.com/2015/06/on-oauth-token-hijacks-for-fun-and.html) by Antonio Sanso
- [Holy redirect_uri Batman, Google tokens leak](http://blog.intothesymmetry.com/2016/05/holy-redirecturi-batman.html) by Antonio Sanso
- [Obtaining Login Tokens for an Outlook, Office or Azure Account](https://whitton.io/articles/obtaining-tokens-outlook-office-azure-account/) by Jack Whitton
- [Yahoo Bug Bounty: Exploiting OAuth Misconfiguration To Takeover Flickr Accounts](https://mishresec.wordpress.com/2017/10/12/yahoo-bug-bounty-exploiting-oauth-misconfiguration-to-takeover-flickr-accounts/) by mishre
- [Flickr ATO Fix Bypass](https://ngailong.wordpress.com/2017/08/07/flickr-ato-fix-bypass/) by Ron Chan
- [One More Thing to Check for SSO – Flickr ATO](https://ngailong.wordpress.com/2017/08/29/one-more-thing-to-check-for-sso-flickr-ato/) by Ron Chan
- [Yahoo Bug Bounty: Chaining 3 Minor Issues To Takeover Flickr Accounts](https://mishresec.wordpress.com/2017/10/13/yahoo-bug-bounty-chaining-3-minor-issues-to-takeover-flickr-accounts/) by mishre
- [Stealing $10,000 Yahoo Cookies!](https://blog.witcoat.com/2018/05/30/stealing-10000-yahoo-cookies/) by Bull
- [Login CSRF + Open Redirect = Uber Account Take Over](https://ngailong.wordpress.com/2017/08/07/uber-login-csrf-open-redirect-account-takeover/) by Ron Chan
- [Uber - redirect_uri is difficult to do it right](https://ngailong.wordpress.com/2017/11/22/uber-redirect_uri-is-difficult-to-do-it-right/) by Ron Chan
- [Authentication bypass on Airbnb via OAuth tokens theft](https://www.arneswinnen.net/2017/06/authentication-bypass-on-airbnb-via-oauth-tokens-theft/) by Arne Swinnen
- [All your Paypal OAuth tokens belong to me - localhost for the win](http://blog.intothesymmetry.com/2016/11/all-your-paypal-tokens-belong-to-me.html) by Antonio Sanso
- [How I made LastPass give me all your passwords](https://labs.detectify.com/2016/07/27/how-i-made-lastpass-give-me-all-your-passwords/) by Mathias Karlsson
- [Hacking Slack using postMessage and WebSocket-reconnect to steal your precious token](https://labs.detectify.com/2017/02/28/hacking-slack-using-postmessage-and-websocket-reconnect-to-steal-your-precious-token/) by Frans Rosén
- [Chaining Self XSS with UI Redressing is Leading to Session Hijacking (PWN users like a boss)](https://medium.com/bugbountywriteup/chaining-self-xss-with-ui-redressing-is-leading-to-session-hijacking-pwn-users-like-a-boss-efb46249cd14) by Armaan Pathan
- [Hacking OAuth2.0 For Fun And Profit](https://drive.google.com/file/d/1Qw3hhValdRAWNGJtLbbFYfKtaevkw4fQ/view) by Pranav Hivarekar
- [Oauth 2.0 redirection bypass cheat sheet](http://nbsriharsha.blogspot.com/2016/04/oauth-20-redirection-bypass-cheat-sheet.html) by nbsriharsha
- [CVV #2: Open Redirect](https://medium.com/bugbountywriteup/cvv-2-open-redirect-213555765607) by SI9INT
- [How I find Open-Redirect Vulnerability in redacted.com (One of the top online payment processing service website)](https://medium.com/@protector47/how-i-find-open-redirect-vulnerability-in-redacted-com-one-of-the-top-payment-gateway-e9b92afdc114) by M.Asim Shahzad
- [Full Account Takeover via Referer Header (OAuth token Steal, Open Redirect Vulnerability Chaining)](https://medium.com/@protector47/full-account-takeover-via-referrer-header-oauth-token-steal-open-redirect-vulnerability-chaining-324a14a1567) by M.Asim Shahzad

### Business Logic Flaw

- [Facebook - bypass ads account's roles vulnerability 2015](https://blog.darabi.me/2015/03/facebook-bypass-ads-account-roles.html) by POUYA DARABI
- [How I Could Steal Money from Instagram, Google and Microsoft](https://www.arneswinnen.net/2016/07/how-i-could-steal-money-from-instagram-google-and-microsoft/) by Arne Swinnen
- [Abusing Multistage Logic Flaw to Buy Anything for Free at hk.deals.yahoo.com](http://web.archive.org/web/20161024050917/http://ngailong.com/abusing-multistage-logic-flaw-to-buy-anything-for-free-at-hk-deals-yahoo-com/) by Ron Chan
- [How anyone could have used Uber to ride for free](http://www.anandpraka.sh/2017/03/how-anyone-could-have-used-uber-to-ride.html) by Anand Prakash
- [Security Questions are not secure](https://labs.detectify.com/2017/12/20/security-questions-are-not-secure/) by Linus Särud
- [The Unknown Hero-App Logic Bugs](https://medium.com/bug-bounty-hunting/application-logic-bugs-600245fb5bf0) by Circle Ninja
- ["How I was able to shop for free!"- Payment Price Manipulation](https://medium.com/bugbountywriteup/bugbounty-how-i-was-able-to-shop-for-free-payment-price-manipulation-b29355a8e68e) by Avinash Jain
- [How I Could Have Promoted Any Facebook Page For Free](https://medium.com/bugbountywriteup/how-i-could-have-promoted-any-facebook-page-for-free-70b0f4fc0feb) by AneesKhan
- [How I was able to get subscription of $120/year For Free](https://blog.securitybreached.org/2018/05/18/get-subscription-of-120-year-for-free-bug-bounty-poc/) by babayaga47
- [Reject a to-be users invitation via their notification](https://medium.com/@absstbh/simple-idor-to-reject-a-to-be-users-invitation-via-their-notification-ae3b919b0fef) by Abss TBH
- [How I booked a rental house for just 1.00 INR — Price Manipulation in Citrus Pay](https://medium.com/@raghav2039/bug-bounty-how-i-booked-a-rental-house-for-just-1-00-inr-price-manipulation-in-citrus-pay-318ff6e0d8a8) by Raghavendra
- [How I got paid premium plan for free on many popular websites](https://medium.com/@khaled.hassan/how-i-got-paid-premium-plan-for-free-on-many-popular-websites-90e62a52416a) by Khaled Hassan

### HTTP Header Injection

- [RECAPTCHA BYPASS VIA HTTP PARAMETER POLLUTION](https://andresriancho.com/recaptcha-bypass-via-http-parameter-pollution/) by andresriancho
- [CRLF injection on Twitter or why blacklists fail](https://blog.innerht.ml/twitter-crlf-injection/) by filedescriptor
- [Twitter Overflow Trilogy in Twitter](https://blog.innerht.ml/overflow-trilogy/) by filedescriptor
- [How a simple readout of Peter Yaworski’s Web Hacking 101 got me into Microsoft Hall of fame](https://medium.com/bug-bounty-hunting/microsoft-hall-of-fame-by-reading-web-hacking-101-217d7838e3bf) by Circle Ninja
- [Exploiting CRLF Injection can lands into a nice bounty](https://medium.com/bugbountywriteup/bugbounty-exploiting-crlf-injection-can-lands-into-a-nice-bounty-159525a9cb62) by Avinash Jain

### Subdomain Takeover

- [Hostile Subdomain Takeover using Heroku/Github/Desk + more](https://labs.detectify.com/2014/10/21/hostile-subdomain-takeover-using-herokugithubdesk-more/) by detectify
- [Hijacking of abandoned subdomains part 2](https://labs.detectify.com/2014/12/08/hijacking-of-abandoned-subdomains-part-2/) by detectify
- [Hijacking tons of Instapage expired users Domains & Subdomains](http://www.geekboy.ninja/blog/hijacking-tons-of-instapage-expired-users-domains-subdomains/) by geekboy
- [Reading Uber’s Internal Emails - Uber Bug Bounty report worth $10,000](http://blog.pentestnepal.tech/post/149985438982/reading-ubers-internal-emails-uber-bug-bounty) by whitehatnepal
- [How I took over a uber subdomain by doing recon](https://medium.com/bugbountywriteup/4500-bounty-how-i-got-lucky-99d8bc933f75) by Eray Mitrani
- [How I snooped into your private Slack messages - Slack Bug bounty worth $2,500](http://blog.pentestnepal.tech/post/150381068912/how-i-snooped-into-your-private-slack-messages) by uranium238
- [Hundreds of hundreds sub-secdomains hack3d! (including Hacker0ne)](https://medium.com/bugbountywriteup/hundreds-of-hundreds-subdomains-hack3d-including-hacker0ne-ad3acd1c0a44) by Ak1T4
- [Netlify - Subdomain Takeover worth 200$](https://medium.com/@alirazzaq/subdomain-takeover-worth-200-ed73f0a58ffe) by Ali Razzaq
- [Shopify - How to do 55.000+ Subdomain Takeover in a Blink of an Eye](https://medium.com/@thebuckhacker/how-to-do-55-000-subdomain-takeover-in-a-blink-of-an-eye-a94954c3fc75) by buckhacker
- [$4500 Bounty — How I got lucky](https://medium.com/bugbountywriteup/4500-bounty-how-i-got-lucky-99d8bc933f75) by Eray Mitrani
- [Subdomain Takeover: Starbucks points to Azure](https://0xpatrik.com/subdomain-takeover-starbucks/) by Patrik Hudak
- [Subdomain Takeover: Finding Candidates](https://0xpatrik.com/subdomain-takeover-candidates/) by Patrik Hudak
- [Subdomain Takeover: Second Order Bugs](https://0xpatrik.com/second-order-bugs/) by Patrik Hudak

### Local File Inclusion

- [Multiple Company LFI](http://panchocosil.blogspot.com/2017/05/one-cloud-based-local-file-inclusion.html) by panchocosil
- [How we got LFI in apache Drill (Recon like a boss)](https://medium.com/bugbountywriteup/how-we-got-lfi-in-apache-drill-recon-like-a-boss-6f739a79d87d) by Gujjuboy10x00
- [CVV #1: Local File Inclusion](https://medium.com/bugbountywriteup/cvv-1-local-file-inclusion-ebc48e0e479a) by SI9INT
- [API keys leakage, Source code disclosure in India’s largest e-commerce health care company](https://medium.com/bugbountywriteup/bugbounty-api-keys-leakage-source-code-disclosure-in-indias-largest-e-commerce-health-care-c75967392c7e) by Avinash Jain

### Unrestricted File Upload

- [Arbitrary file upload in ubernihao.com](https://medium.com/@daksh_/arbitrary-file-upload-in-ubernihao-com-77ad40a4850a) by Daksh Patel
- [How i Hacked into a PayPal's Server - Unrestricted File Upload to Remote Code Execution](http://web.archive.org/web/20170721135642/http://blog.pentestbegins.com/2017/07/21/hacking-into-paypal-server-remote-code-execution-2017/) by Vikas Anil Sharma
- [RBookFresh Tricky File Upload Bypass to RCE](https://www.secgeek.net/bookfresh-vulnerability/) by secgeek

### Brute Force

- [How I could have hacked all Facebook accounts](http://www.anandpraka.sh/2016/03/how-i-could-have-hacked-your-facebook.html) by Anand Prakash
- [Facebook Account Take Over by using SMS verification code](https://arunsureshkumar.me/index.php/2016/04/24/facebook-account-take-over/) by Arun Sureshkumar
- [How I Could Compromise 4% (Locked) Instagram Accounts](https://www.arneswinnen.net/2016/03/how-i-could-compromise-4-locked-instagram-accounts/) by Arne Swinnen
- [InstaBrute: Two Ways to Brute-force Instagram Account Credentials](https://www.arneswinnen.net/2016/05/instabrute-two-ways-to-brute-force-instagram-account-credentials/) by Arne Swinnen
- [How I was able to enumerate Instagram Accounts who had enabled 2FA (Two Step Verification) for additional protection](https://medium.com/@zk34911/facebook-bug-bounty-how-i-was-able-to-enumerate-instagram-accounts-who-had-enabled-2fa-two-step-fddba9e9741c) by zk34911
- [How I could have mass uploaded from every Flickr account](https://ret2got.wordpress.com/2017/10/05/how-i-could-have-mass-uploaded-from-every-flickr-account/) by Jazzy

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

### Remote Code Execution

- [Facebaook Acquisition: Popping a shell on the Oculus developer portal](https://bitquark.co.uk/blog/2014/08/31/popping_a_shell_on_the_oculus_developer_portal) by Bitquark
- [How I Hacked Facebook, and Found Someone's Backdoor Script](http://devco.re/blog/2016/04/21/how-I-hacked-facebook-and-found-someones-backdoor-script-eng-ver/) by Orange Tsai
- [Remote Code Execution on a Facebook server](https://blog.scrt.ch/2018/08/24/remote-code-execution-on-a-facebook-server/) by Daniel Le Gall
- [Command Injection in Google Console](http://www.pranav-venkat.com/2016/03/command-injection-which-got-me-6000.html) by Venkat S
- [GitHub Enterprise Remote Code Execution](https://www.exablue.de/blog/2017-03-15-github-enterprise-remote-code-execution.html) by iblue
- [How I Chained 4 vulnerabilities on GitHub Enterprise, From SSRF Execution Chain to RCE](http://blog.orange.tw/2017/07/how-i-chained-4-vulnerabilities-on.html) by Orange Tsai
- [Yahoo! Remote Command Execution Vulnerability](http://www.sec-down.com/wordpress/?p=87) by Ebrahim Hegazy
- [Yahoo Remote Code Execution on cms.snacktv.de](https://seanmelia.files.wordpress.com/2016/02/yahoo-remote-code-execution-cms1.pdf) by Sean Melia
- [Command Injection in Yahoo Acquisition](http://samcurry.net/how-i-couldve-taken-over-the-production-server-of-a-yahoo-acquisition-through-command-injection/) by samwcyo
- [Remote Code Execution by struct2 Yahoo Server](https://medium.com/@th3g3nt3l/how-i-got-5500-from-yahoo-for-rce-92fffb7145e6) by Th3G3nt3lman
- [Yahoo! RCE via Spring Engine SSTI, Recon Pay Off](https://hawkinsecurity.com/2017/12/13/rce-via-spring-engine-ssti/) by tghawkins
- [RCE on Yahoo Luminate](https://sites.google.com/securifyinc.com/secblogs/yahoo-luminate-rce) by Rojan Rijal
- [How I found 2.9 RCE at Yahoo! Bug Bounty program](https://medium.com/@kedrisec/how-i-found-2-9-rce-at-yahoo-bug-bounty-program-20ab50dbfac7) by Kedrisec
- [Airbnb – Ruby on Rails String Interpolation led to Remote Code Execution](https://buer.haus/2017/03/13/airbnb-ruby-on-rails-string-interpolation-led-to-remote-code-execution/) by Brett Buerhaus
- [How we broke PHP, hacked Pornhub and earned $20,000](https://www.evonide.com/how-we-broke-php-hacked-pornhub-and-earned-20000-dollar/) by Ruslan Habalov
  - *Alert*, God-like Write-up, make sure you know what is ROP before clicking, which I don't =(
- [How I hacked Pornhub for fun and profit - 10,000$](https://5haked.blogspot.sg/) by 5haked
- [PayPal Node.js code injection (RCE)](http://artsploit.blogspot.com/2016/08/pprce2.html) by Michael Stepankin
- [Magento Remote Code Execution Vulnerability!](http://www.sec-down.com/wordpress/?p=578) by Ebrahim Hegazy
- [Telekom.de Remote Command Execution!](http://www.sec-down.com/wordpress/?p=581) by Ebrahim Hegazy
- [LFI to Command Execution: Deutche Telekom Bug Bounty](https://medium.com/@maxon3/lfi-to-command-execution-deutche-telekom-bug-bounty-6fe0de7df7a6) by Daniel Maksimovic
- [Command Injection Vulnerability in Hostinger](http://elladodelnovato.blogspot.com/2017/02/command-injection-vulnerability-in.html) by Alberto Segura
- [$20k RCE in Jenkin Instance](http://nahamsec.com/secure-your-jenkins-instance-or-hackers-will-force-you-to/) by Ben Sadeghipour
- [$50k RCE in JetBrains IDE](http://blog.saynotolinux.com/blog/2016/08/15/jetbrains-ide-remote-code-execution-and-local-file-disclosure-vulnerability-analysis/) by Jordan Milne
- [Pentest: 0day in iTop 2.4.0 gave me Domain Admin Priviledges](https://httpsonly.blogspot.com/2018/04/pentest-0day-in-itop-240-gave-me-domain.html) by httpsonly
- [RCE due to ShowExceptions](https://sites.google.com/view/harshjaiswalblog/rce-due-to-showexceptions) by Harsh Jaiswal
- [How I Chained 4 Bugs(Features?) into RCE on Amazon Collaboration System](http://blog.orange.tw/2018/08/how-i-chained-4-bugs-features-into-rce-on-amazon.html) by Orange Tsai
- [Server-Side Template Injection](https://portswigger.net/blog/server-side-template-injection) by James Kettle
- [RCE due to ShowExceptions](https://sites.google.com/view/harshjaiswalblog/rce-due-to-showexceptions) by Harsh Jaiswal
- [RCE Unsecure Jenkins Instance](https://blog.securitybreached.org/2018/09/07/rce-jenkins-instance-dosomething-org-bug-bounty-poc/) by babayaga47
- [FROM SHODAN TO REMOTE CODE EXECUTION #1 – HACKING JENKINS](https://the-infosec.com/2017/06/22/from-shodan-to-remote-code-execution-1-hacking-jenkins/) by emenalf
- [FROM SHODAN TO REMOTE CODE EXECUTION #2 – HACKING OPENDREAMBOX 2.0.0](https://the-infosec.com/2017/05/12/from-shodan-to-rce-opendreambox-2-0-0-code-execution/) by emenalf
- [From finding Jenkins instance to Command Execution](https://medium.com/@logicbomb_1/bugbounty-from-finding-jenkins-instance-to-command-execution-secure-your-jenkins-instance-9bd1e75c2288) by Avinash Jain
- [How I got hall of fame in two fortune 500 companies — An RCE story](https://medium.com/@emenalf/how-i-got-hall-of-fame-in-two-fortune-500-companies-an-rce-story-9c89cead81ff) by Alfie
- [No RCE? Then SSH to the box!](http://blog.jr0ch17.com/2018/No-RCE-then-SSH-to-the-box/) by Jasmin Landry
- ["Journey from LFI to RCE"-How I was able to get the same in one of the India’s popular property buy/sell company](https://medium.com/bugbountywriteup/bugbounty-journey-from-lfi-to-rce-how-a69afe5a0899) by Avinash Jain
- [How I was able to bypass firewall to get RCE and then went from server shell to get root user account](https://medium.com/@logicbomb_1/bugbounty-how-i-was-able-to-bypass-firewall-to-get-rce-and-then-went-from-server-shell-to-get-783f71131b94) by Avinash Jain
- [GETTING PHP CODE EXECUTION AND LEVERAGE ACCESS TO PANELS,DATABASES,SERVER](https://www.shawarkhan.com/2018/06/getting-php-code-execution-and-leverage.html) by SHAWAR KHAN
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

- [Top 10 Web Hacking Techniques of 2017 - Nominations Open](https://portswigger.net/blog/top-10-web-hacking-techniques-of-2017-nominations-open) by James Kettle
- [Top 10 Web Hacking Techniques of 2017](https://portswigger.net/blog/top-10-web-hacking-techniques-of-2017)  by James Kettle
- [Top 10 web hacking techniques of 2018 - nominations open](https://portswigger.net/blog/top-10-web-hacking-techniques-of-2018-nominations-open) by James Kettle
- [Web Application Penetration Testing Course](https://docs.google.com/document/d/101EsKlu41ICdeE7mEv189SS8wMtcdXfRtua0ClYjP1M/edit)
- [List of bug bounty writeups](https://pentester.land/list-of-bug-bounty-writeups.html)
- [CTF write up, Great for Bug Bounty](https://ctftime.org/writeups?tags=web200&hidden-tags=web%2cweb100%2cweb200)
- [Smart Contract Vulnerabilities](http://www.dasp.co/)
- [Tutorials](https://securityidiots.com/) by Security Idiots
- [HACKING NODEJS AND MONGODB](https://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html) by websecurify
- [Mongo DB Injection again](https://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html) by websecrify
- [Jumping to The Hell With 10 Attempts to Bypass Devil's WAF](https://medium.com/bugbountywriteup/jumping-to-the-hell-with-10-attempts-to-bypass-devils-waf-4275bfe679dd) by Ak1T4
- [High Risk Vulnerabilities within the DoD - Exploiting Coldfusion, Dotnet Nuke, Oracle, and more](https://medium.com/@alyssa.o.herrera/high-risk-vulnerabilities-within-the-dod-from-coldfusion-dotnet-nuke-oracle-and-more-cc730f748c69) by Alyssa Herrera
- [A penetration tester’s guide to sub-domain enumeration](https://blog.appsecco.com/a-penetration-testers-guide-to-sub-domain-enumeration-7d842d5570f6) by Bharath
- [Static Analysis of Client-Side JavaScript for pen testers and bug bounty hunters](https://blog.appsecco.com/static-analysis-of-client-side-javascript-for-pen-testers-and-bug-bounty-hunters-f1cb1a5d5288) by Bharath
- [Escalating low severity bugs to high](https://www.noob.ninja/2018/07/escalating-low-severity-bugs-to-high.html) by Noob Ninja
- [How I earned 60K+ from private program](https://medium.com/@sivakrishnasamireddi/how-i-earned-60k-from-private-program-71bd51554490) by Siva Krishna Samireddi
- [Just another tale of severe bugs on a private program](https://medium.com/@sivakrishnasamireddi/just-another-tale-of-severe-bugs-on-a-private-program-405870b03532) by Siva Krishna Samireddi
- [How to Hack WebSockets and Socket.io](https://www.blackhillsinfosec.com/how-to-hack-websockets-and-socket-io/) by Ethan Robish
- [How to perform the static analysis of website source code with the browser — the beginner’s bug bounty hunters guide](https://medium.com/@_bl4de/how-to-perform-the-static-analysis-of-website-source-code-with-the-browser-the-beginners-bug-d674828c8d9a) by bl4de
- [ZERO-DAY RCE VIA XXE & SSRF ON NETGEAR STORA, SEAGATE HOME, AND MEDION LIFECLOUD NAS](http://www.paulosyibelo.com/2018/11/zero-day-rce-via-xxe-ssrf-on-netgear.html) by Paulos Yibelo
- [Google bug bounty for security exploit that influences search results](http://www.tomanthony.co.uk/blog/google-xml-sitemap-auth-bypass-black-hat-seo-bug-bounty/) by Tom
- [Why Facebook's api starts with a for loop](https://dev.to/antogarand/why-facebooks-api-starts-with-a-for-loop-1eob) by Antony Garand
- [Whitepaper: HTTP Security Headers and How They Work](https://www.netsparker.com/whitepaper-http-security-headers/) by Ziyahan Albeniz, Sven Morgenroth, Umran Yildirimkaya
- [WEB APPLICATION PENETRATION TESTING NOTES](https://techvomit.net/web-application-penetration-testing-notes/) by Tech Vomit
- [Extreme details in vulnerablities detecting](https://medium.com/@jonathanbouman) by Jonathan Bouman
- [Advanced JavaScript Injections](https://brutelogic.com.br/blog/advanced-javascript-injections/) by Brute
- [Bypass CSP by Abusing XSS Filter in Edge](https://medium.com/bugbountywriteup/bypass-csp-by-abusing-xss-filter-in-edge-43e9106a9754) by Xiaoyin Liu

### Exclusive Bugbounty Writeup Blog

- [10 Interesting Vulnerabilities in Instagram](https://www.arneswinnen.net/2016/02/the-tales-of-a-bug-bounty-hunter-10-interesting-vulnerabilities-in-instagram/) by Arne Swinnen
- [A list of FB writeup collected by phwd](http://web.archive.org/web/20171220084758/https://www.facebook.com/notes/phwd/facebook-bug-bounties/707217202701640) by phwd
- [Facebook Bugbounty Writeup Blog](https://philippeharewood.com) by phwd
- [Google Bugbouty Writeup](https://sites.google.com/site/testsitehacking/write-ups) by eze2307
- [Clickjackings in Google](https://medium.com/@raushanraj_65039/google-clickjacking-6a04132b918a) by Raushan Raj
- [Clickjacking in Google Docs and Voice typing feature](https://medium.com/@raushanraj_65039/clickjacking-in-google-docs-and-voice-typing-feature-c481d00b020a) by Raushan Raj
- [Clickjacking on Google MyAccount Worth 7,500$](https://apapedulimu.click/clickjacking-on-google-myaccount-worth-7500/) by Apapedulimu
- [Google VRP Writeups](https://sites.google.com/securifyinc.com/vrp-writeups/home?authuser=0) by securifyinc
- [XS-Searching Google’s bug tracker to find out vulnerable source code](https://medium.com/@luanherrera/xs-searching-googles-bug-tracker-to-find-out-vulnerable-source-code-50d8135b7549) by Luan Herrera
- [Uber - Another "TicketTrick" story](https://sites.google.com/securifyinc.com/secblogs/uber-business-support-bug?authuser=0) by securifyinc
- [Shopify Athena Bug](https://sites.google.com/securifyinc.com/secblogs/shopify-athena-bug?authuser=0) by securifyinc
- [Bug Bounty: Fastmail](https://medium.com/bugbountywriteup/bug-bounty-fastmail-feeda67905f5) by hyde

### Interesting but Seems Not Applicable Now
- [RPO that lead to information leakage in Google](http://blog.innerht.ml/rpo-gadgets/) by filedescriptor
- [IE & Edge URL Parsing Problem](https://labs.detectify.com/2016/10/24/combining-host-header-injection-and-lax-host-parsing-serving-malicious-data/) - by detectify
- [xss in Google by IE Weird Behavior](http://blog.bentkowski.info/2015/04/xss-via-host-header-cse.html)
- [Internet Explorer Has a URL Parsing Problem](https://blog.innerht.ml/internet-explorer-has-a-url-problem/) by Jigsaw
- [XSS by Tossing Cookies in Microsoft and Twitter](http://blog.wesecureapp.com/xss-by-tossing-cookies/) by Akhil Reni
- [How I could Steal Your Google Bug Hunter Account with Two Clicks in IE](https://ngailong.wordpress.com/2017/08/07/how-i-could-steal-your-google-bug-hunter-account-with-two-clicks-in-ie/) by Ron Chan
