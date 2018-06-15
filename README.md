# Bug Bounty Reference

A list of bug bounty write-up that is categorized by the bug nature, this is inspired by https://github.com/djadmin/awesome-bug-bounty

# Introduction

I have been reading for Bug Bounty write-ups for a few months, I found it extremely useful to read relevant write-up when I found a certain type of vulnerability that I have no idea how to exploit. Let say you found a RPO (Relativce Path Overwrite) in a website, but you have no idea how should you exploit that, then the perfect place to go would be [here](https://blog.innerht.ml/rpo-gadgets/). Or you have found your customer is using oauth mechanism but you have no idea how should we test it, the other perfect place to go would be [here](https://whitton.io/articles/obtaining-tokens-outlook-office-azure-account/)

My intention is to make a full and complete list of common vulnerability that are publicly disclosed bug bounty write-up, and let Bug Bounty Hunter to use this page as a reference when they want to gain some insight for a particular kind of vulnerability during Bug Hunting, feel free to submit pull request. Okay, enough for chit-chatting, let's get started. 


- [XSSI](#xssi)
- [Cross-Site Scripting (XSS)](#cross-site-scripting-xss)
- [Brute Force](#brute-force)
- [SQL Injection (SQLi)](#sql-injection)
- [External XML Entity Attack (XXE)](#xxe)
- [Remote Code Execution (RCE)](#remote-code-execution)
  - [Deserialization](#deserialization)
  - [Image Tragick](#image-tragick)
- [Cross-Site Request Forgery (CSRF)](#csrf)
- [Insecure Direct Object Reference (IDOR)](#insecure-direct-object-reference-idor)
- [Stealing Access Token](#stealing-access-token)
  - [Google Oauth Login Bypass](#google-oauth-bypass)
- [Server Side Request Forgery (SSRF)](#server-side-request-forgery-ssrf)
- [Unrestricted File Upload](#unrestricted-file-upload)
- [Race Condition](#race-condition)
- [Business Logic Flaw](#business-logic-flaw)
- [Authentication Bypass](#authentication-bypass)
- [HTTP Header Injection](#http-header-injection)
- [Email Related](#email-related)
- [Money Stealing](#money-stealing)
- [Miscellaneous](#miscellaneous)


### Cross-Site Scripting (XSS)

- [Three Interesting Stored XSS in Facebook](http://www.breaksec.com/?p=6129) by Nirgoldshlager
- [An XSS on Facebook via PNGs & Wonky Content Types](https://whitton.io/articles/xss-on-facebook-via-png-content-types/) by Jack Whitton
  - he is able to make stored XSS from a irrelevant domain to main facebook domain 
- [Stored XSSes in Facebook Wall by Embedding an External Video with Open Graph](https://opnsec.com/2018/03/stored-xss-on-facebook/) by opnsec
- [Stored XSS in Google Drive (Folder Name)](https://pwnrules.com/google-drive-stored-xss/)
- [XSS in Youtube, Google Translate, Google Docs](https://labs.detectify.com/2015/06/06/google-xss-turkey/) by fransrosen
- [Drag-Drop XSS in Google Docs Drawing Moudle](http://c0rni3sm.blogspot.com/2016/04/drag-drop-xss-in-google.html) by p0pc0rn
- [Stored, Reflected and DOM XSS in Google for Work Connect (GWC)](http://respectxss.blogspot.com/2016/02/stored-reflected-and-dom-xss-in-google.html) by Ashar Javed
- [Sleeping stored Google XSS Awakens a $5000 Bounty](https://blog.it-securityguard.com/bugbounty-sleeping-stored-google-xss-awakens-a-5000-bounty/) by Patrik Fehrenbach
- [Subdomain Clickjacking in Google Trigger DOM XSS](http://sasi2103.blogspot.sg/2016/09/combination-of-techniques-lead-to-dom.html) by Sasi
- [How I found a $5,000 Google Maps XSS (by fiddling with Protobuf)](https://medium.com/@marin_m/how-i-found-a-5-000-google-maps-xss-by-fiddling-with-protobuf-963ee0d9caff#.cktt61q9g) by Marin MoulinierFollow
- [Google Japan Book XSS](http://nootropic.me/blog/en/blog/2016/09/20/%E3%82%84%E3%81%AF%E3%82%8A%E3%83%8D%E3%83%83%E3%83%88%E3%82%B5%E3%83%BC%E3%83%95%E3%82%A3%E3%83%B3%E3%82%92%E3%81%97%E3%81%A6%E3%81%84%E3%81%9F%E3%82%89%E3%81%9F%E3%81%BE%E3%81%9F%E3%81%BEgoogle/)
- [Use Two Open Redirects to Trigger an XSS](https://sites.google.com/site/bughunteruniversity/best-reports/openredirectsthatmatter) by Tomasz Bojarski
- [Managed Apps and Music: two Google reflected XSSes](https://ysx.me.uk/managed-apps-and-music-a-tale-of-two-xsses-in-google-play/) by Yasin Soliman
- [App Maker and Colaboratory: two Google stored XSSes](https://ysx.me.uk/app-maker-and-colaboratory-a-stored-google-xss-double-bill/) by Yasin Soliman
- [Stored XSS in Google Adwords](https://medium.com/@Alra3ees/google-adwords-3133-7-stored-xss-27bb083b8d27) by Emad Shanab
- [Stored XSS, and SSRF in Google using the Dataset Publishing Language](https://s1gnalcha0s.github.io/dspl/2018/03/07/Stored-XSS-and-SSRF-Google.html) by Signal Chaos
- [Yahoo Mail stored XSS](https://klikki.fi/adv/yahoo.html) by Jouko Pynnönen
- [xss in Yahoo Mail Again, worth $10000](https://klikki.fi/adv/yahoo2.html) by Jouko Pynnönen
- [xss in Yahoo Fantasy Sport](https://web.archive.org/web/20161228182923/http://dawgyg.com/2016/12/07/stored-xss-affecting-all-fantasy-sports-fantasysports-yahoo-com-2/) by thedawgyg
- [Login-Logout-Login: Turning Self-XSS into Good XSS in Uber](https://whitton.io/articles/uber-turning-self-xss-into-good-xss/) by Jack Whitton
- [Turning Self-XSS into Good XSS in Uber v2: Chanllenge Completed but Not Rewarded](https://httpsonly.blogspot.hk/2016/08/turning-self-xss-into-good-xss-v2.html) by httpsonly
- [DOM XSS - auth.uber.com](http://stamone-bug-bounty.blogspot.com/2017/10/dom-xss-auth_14.html) by StamOne
- [AirBnb Bug Bounty: Turning Self-XSS in Ture-Client-IP Header into Good-XSS #2](http://www.geekboy.ninja/blog/airbnb-bug-bounty-turning-self-xss-into-good-xss-2/) by geekboy
- [XSS due to Improper Regex in Third Party JS in Uber](http://zhchbin.github.io/2016/09/10/A-Valuable-XSS/) by Chaobin Zhang
- [XSS in Uber via Cookie](http://zhchbin.github.io/2017/08/30/Uber-XSS-via-Cookie/) by Chaobin Zhang
- [Airbnb – When Bypassing JSON Encoding, XSS Filter, WAF, CSP, and Auditor turns into Eight Vulnerabilities](https://buer.haus/2017/03/08/airbnb-when-bypassing-json-encoding-xss-filter-waf-csp-and-auditor-turns-into-eight-vulnerabilities/) by Brett Buerhaus
- [Twitter XSS by Stopping Redirection and Javascript Scheme](http://blog.blackfan.ru/2017/09/devtwittercom-xss.html) by Sergey Bobrov
- [Persistent XSS to Steal Passwords in Paypal](https://wesecureapp.com/blog/persistent-xss-to-steal-passwords-paypal/) by Akhil Reni
- [Stored XSS on myworld.ebay.com](https://whitton.io/archive/persistent-xss-on-myworld-ebay-com/) by Jack Whitton
- [Use CSRF to Turn Self-XSS into XSS in A Browser's Extention by Indeed.com](http://c0rni3sm.blogspot.com/) by p0pc0rn
- [Stored XSS on Snapchat](https://medium.com/@mrityunjoy/stored-xss-on-snapchat-5d704131d8fd) by Mrityunjoy
- [XSS on Bugcrowd and so many other website's main Domain](http://witcoat.blogspot.com/2017/06/xss-on-bugcrowd-and-so-many-other.html) by Bull

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
- [How i Hacked your Beats account ? Apple Bug Bounty](https://aadityapurani.com/2016/07/20/how-i-hacked-your-beats-account-apple-bug-bounty/) by Additya Purani

## Cross-Site Script Inclusion (XSSI)

- [OWASP XSSI](https://www.owasp.org/images/f/f3/Your_Script_in_My_Page_What_Could_Possibly_Go_Wrong_-_Sebastian_Lekies%2BBen_Stock.pdf) by Sebastian Lekies and Ben Stock
- [Backdoor of All Flickr API Calls by XSSI](https://ngailong.wordpress.com/2017/08/11/open-door-to-all-flickr-api-calls-by-xssi/) by Ron Chan

### Server Side Request Forgery (SSRF)

- [SSRF to query google internal server](https://www.rcesecurity.com/2017/03/ok-google-give-me-all-your-internal-dns-information/) by rcesecurity
- [When Server Side Request Forgery combine with Cross Site Scripting](http://web.archive.org/web/20170218205059/http://ngailong.com/what-could-happen-when-server-side-request-forgery-combine-with-cross-site-scripting/) by Ron Chan
- [Airbnb – Chaining Third-Party Open Redirect into Server-Side Request Forgery (SSRF) via LivePerson Chat](https://buer.haus/2017/03/09/airbnb-chaining-third-party-open-redirect-into-server-side-request-forgery-ssrf-via-liveperson-chat/) by Brett Buerhaus
- [SSRF tips from BugBountyHQ of Images - Open Graph Protocol is a good case for Blind SSRF / Extract of Meta Data](https://twitter.com/BugBountyHQ/status/868242771617792000) by BugBountyHQ
- [SSRF to LFI](https://seanmelia.wordpress.com/2015/12/23/various-server-side-request-forgery-issues/) by seanmelia
- [SSRF to pivot internal network](https://seanmelia.files.wordpress.com/2016/07/ssrf-to-pivot-internal-networks.pdf) by seanmelia
- [ESEA Server-Side Request Forgery and Querying AWS Meta Data](https://buer.haus/2016/04/18/esea-server-side-request-forgery-and-querying-aws-meta-data/) by Brett Buerhaus
- [Pivoting fromm Blind SSRF to RCE](http://www.kernelpicnic.net/2017/05/29/Pivoting-from-blind-SSRF-to-RCE-with-Hashicorp-Consul.html) by Peter Adkins
- [Plotly AWS EC2 Metadata Disclosure via SSRF and a Stored XSS via Presentation Link)](https://ysx.me.uk/a-pair-of-plotly-bugs-stored-xss-and-aws-metadata-ssrf/) by Yasin Soliman
- [Blog post: Cracking the Lens: Targeting HTTP’s Hidden Attack-Surface ](https://portswigger.net/blog/cracking-the-lens-targeting-https-hidden-attack-surface) by James Kettle

### XXE

- [How we got read access on Google’s production servers](https://blog.detectify.com/2014/04/11/how-we-got-read-access-on-googles-production-servers/) by  detectify
- [Blind OOB XXE At UBER 26+ Domains Hacked](http://nerdint.blogspot.hk/2016/08/blind-oob-xxe-at-uber-26-domains-hacked.html) by Raghav Bisht
- [0day in Code42 - XXE in uber.com to read local files](https://httpsonly.blogspot.com/2017/01/0day-writeup-xxe-in-ubercom.html) by httpsonly
- [XXE through SAML](https://seanmelia.files.wordpress.com/2016/01/out-of-band-xml-external-entity-injection-via-saml-redacted.pdf) by seanmelia
- [XXE by SVG in Lithium Community Platform](http://esoln.net/Research/2017/03/30/xxe-in-lithium-community-platform/) by Vibhuti Nath

### Direct Object Reference (IDOR)

- [Hacking Facebook.com/thanks Posting on behalf of your friends!](http://www.anandpraka.sh/2014/11/hacking-facebookcomthanks-posting-on.html) by Anand Prakash
- [Change the description of a video without publish_actions permission in Facebook](https://philippeharewood.com/change-the-description-of-a-video-without-publish_actions-permission/) by phwd
- [How I could have removed all your Facebook notes](http://www.anandpraka.sh/2015/12/summary-this-blog-post-is-about.html) by Anand Prakash
- [Overwriting/Removing Cover Photos on Facebook Event Pages](http://roy-castillo.blogspot.com/2016/02/overwritingremoving-cover-photos-on.html) by Roy Castillo
- [IDOR inf Facebook's Acquisition - Parse](http://www.pranav-venkat.com/2016/12/idor-in-facebooks-acquisition-parse.html) by Venkat S
- [Delete any video from Facebook](https://pranavhivarekar.in/2016/06/23/facebooks-bug-delete-any-video-from-facebook/) by PRANAV HIVAREKAR
- [Delete Any Video on Facebook](https://danmelamed.blogspot.com/2017/01/facebook-vulnerability-delete-any-video.html) by Dan Melamed
- [Image removal vulnerability in Facebook polling feature](https://blog.darabi.me/2017/11/image-removal-vulnerability-in-facebook.html) by Pouya Darabi
- [Facebook Page Takeover by Manipulating the Parameter](https://arunsureshkumar.me/index.php/2016/09/16/facebook-page-takeover-zero-day-vulnerability/) by Arun Sureshkumar
- [Vulnerability in Youtube allowed moving comments from any video to another](https://www.secgeek.net/youtube-vulnerability/) by secgeek
  - It's *Google* Vulnerability, so it's worth reading, as generally it is more difficult to find Google vulnerability
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

### Sensitive Data Exposure

- [FB users birth year disclosed via FB Timeline profile source code “data attribute”](https://medium.com/@rajsek/curiosity-and-passion-to-your-profession-might-lead-to-make-your-dream-come-true-7d9be3c6029a) by Raja Sekar Durairaj
- [FB user birth year Disclosure via “IDOR in m.facebook.com”](https://medium.com/@rajsek/my-2nd-facebook-bounty-poc-fb-data-of-birth-disclosure-d02e1bec50) by Raja Sekar Durairaj
- [DOB disclosed using “Facebook Graph API Reverse Engineering”](https://medium.com/@rajsek/my-3rd-facebook-bounty-hat-trick-chennai-tcs-er-name-listed-in-facebook-hall-of-fame-47f57f2a4f71#.9gbtbv42q) by Raja Sekar Durairaj
- [Abusing Facebook Graph Search using GraphQL](https://philippeharewood.com/abusing-facebook-graph-search/) by phwd
- [Facebook's Bug - Fooling Graph Search to Bypass Privacy Restrictions & Extract Private Information](https://pranavhivarekar.in/2016/02/20/facebooks-bug-fooling-graph-search-to-bypass-privacy-restrictions/) by PRANAV HIVAREKAR
- [Unauthorized access to credit/prepaid card details (limited) of any user](https://pranavhivarekar.in/2017/02/11/facebooks-bug-unauthorized-access-to-credit-card-details-limited-of-any-user/) by PRANAV HIVAREKAR
- [Getting any Facebook User's Friend List and Partial Payment Card Details](https://www.josipfranjkovic.com/blog/facebook-friendlist-paymentcard-leak) by JOSIP FRANJKOVIĆ

### Authentication Bypass

- [How I could have hacked all Facebook accounts](http://www.anandpraka.sh/2016/03/how-i-could-have-hacked-your-facebook.html) by Anand Prakash
- [Facebook Account Take Over](https://arunsureshkumar.me/index.php/2016/04/24/facebook-account-take-over/) by Arun Sureshkumar
- [Taking over Facebook Accounts using Free Basics Partner Portal](https://www.josipfranjkovic.com/blog/facebook-partners-portal-account-takeover) by JOSIP FRANJKOVIĆ
- [Hacking Facebook’s Legacy API, Part 1: Making Calls on Behalf of Any User](https://stephensclafani.com/2014/07/08/hacking-facebooks-legacy-api-part-1-making-calls-on-behalf-of-any-user/) by Stephen Sclafani
- [Hacking Facebook’s Legacy API, Part 2: Stealing User Sessions](https://stephensclafani.com/2014/07/29/hacking-facebooks-legacy-api-part-2-stealing-user-sessions/) by Stephen Sclafani
- [Use XSS and Bug Chain to Bypass Google Account Recovery Restriction](https://sites.google.com/site/bughunteruniversity/best-reports/account-recovery-xss) by Ramzes
- [Bypassing Google Authentication on Periscope's Administration Panel](https://whitton.io/articles/bypassing-google-authentication-on-periscopes-admin-panel/) By Jack Whitton
- [Bypassing Google Email Domain Check to Deliver Spam Email on Google’s Behalf](http://web.archive.org/web/20161209085817/http://ngailong.com/bypassing-google-email-domain-check-to-deliver-spam-email-on-googles-behalf/) by Ron Chan
- [Office365 Auth Bypass - The road to hell is paved with SAML Assertions](http://www.economyofmechanism.com/office365-authbypass.html) by Yiannis Kakavas
- [Github SAML - The road to your codebase is paved with forged assertions](http://www.economyofmechanism.com/github-saml.html) by Yiannis Kakavas
- [Authentication bypass on Uber’s Single Sign-On via subdomain takeover](https://www.arneswinnen.net/2017/06/authentication-bypass-on-ubers-sso-via-subdomain-takeover/) by Arne Swinnen
- [Uber Bug Bounty: Gaining Access To An Internal Chat System](https://mishresec.wordpress.com/2017/10/13/uber-bug-bounty-gaining-access-to-an-internal-chat-system/) by mishre
- [2FA PayPal Bypass](https://henryhoggard.co.uk/blog/Paypal-2FA-Bypass) by henryhoggard
- [Decoding a .htpasswd to Earn a Payload of Money](https://blog.it-securityguard.com/bugbounty-decoding-a-%F0%9F%98%B1-00000-htpasswd-bounty/) by Patrik Fehrenbach
- [Slack SAML authentication bypass](http://blog.intothesymmetry.com/2017/10/slack-saml-authentication-bypass.html) by Antonio Sanso
- [From JS to another JS files lead to authentication bypass](http://c0rni3sm.blogspot.com/2017/06/from-js-to-another-js-files-lead-to.html) by c0rni3sm
- [Accidentally typo to bypass administration access](http://c0rni3sm.blogspot.com/2017/08/accidentally-typo-to-bypass.html) by c0rni3sm
- [Response To Request Injection (RTRI)](http://web.archive.org/web/20160907083447/https://www.bugbountyhq.com/front/latestnews/dWRWR0thQ2ZWOFN5cTE1cXQrSFZmUT09/) by ?
  - be honest, thanks to this article, I have found quite a few bugs because of using his method, respect to the author!

### Stealing Access Token

- [Facebook Access Token Stolen](https://whitton.io/articles/stealing-facebook-access-tokens-with-a-double-submit/) by Jack Whitton
- [Stealing Facebook Messenger Login Nonces worth 15k](https://stephensclafani.com/2017/03/21/stealing-messenger-com-login-nonces/) by Stephen Sclafani
- [Stealing Facebook access_tokens Using CSRF in Device Login Flow](https://www.josipfranjkovic.com/blog/hacking-facebook-csrf-device-login-flow) by JOSIP FRANJKOVIĆ
- [Steal Oculus Nonce and Oauth Flow Bypass](https://medium.com/@lokeshdlk77/bypass-oauth-nonce-and-steal-oculus-response-code-faa9cc8d0d37)
- [A tale about appengine.google.com authentication and life](https://proximasec.blogspot.com/2017/02/a-tale-about-appengines-authentication.html) by Andrey's Ramblings
- [Steal Google Oauth in Microsoft](http://blog.intothesymmetry.com/2015/06/on-oauth-token-hijacks-for-fun-and.html) by Antonio Sanso
- [Holy redirect_uri Batman, Google tokens leak](http://blog.intothesymmetry.com/2016/05/holy-redirecturi-batman.html) by Antonio Sanso
- [Obtaining Login Tokens for an Outlook, Office or Azure Account](https://whitton.io/articles/obtaining-tokens-outlook-office-azure-account/) by Jack Whitton
- [Yahoo Bug Bounty: Exploiting OAuth Misconfiguration To Takeover Flickr Accounts](https://mishresec.wordpress.com/2017/10/12/yahoo-bug-bounty-exploiting-oauth-misconfiguration-to-takeover-flickr-accounts/) by mishre
- [Flickr ATO Fix Bypass](https://ngailong.wordpress.com/2017/08/07/flickr-ato-fix-bypass/) by Ron Chan
- [One More Thing to Check for SSO – Flickr ATO](https://ngailong.wordpress.com/2017/08/29/one-more-thing-to-check-for-sso-flickr-ato/) by Ron Chan
- [Yahoo Bug Bounty: Chaining 3 Minor Issues To Takeover Flickr Accounts](https://mishresec.wordpress.com/2017/10/13/yahoo-bug-bounty-chaining-3-minor-issues-to-takeover-flickr-accounts/) by mishre
- [Stealing $10,000 Yahoo Cookies!](http://witcoat.blogspot.com/2017/12/stealing-10000-yahoo-cookies.html) by Bull
- [Login CSRF + Open Redirect = Uber Account Take Over](https://ngailong.wordpress.com/2017/08/07/uber-login-csrf-open-redirect-account-takeover/) by Ron Chan
- [Uber - redirect_uri is difficult to do it right](https://ngailong.wordpress.com/2017/11/22/uber-redirect_uri-is-difficult-to-do-it-right/) by Ron Chan
- [Authentication bypass on Airbnb via OAuth tokens theft](https://www.arneswinnen.net/2017/06/authentication-bypass-on-airbnb-via-oauth-tokens-theft/) by Arne Swinnen
- [All your Paypal OAuth tokens belong to me - localhost for the win](http://blog.intothesymmetry.com/2016/11/all-your-paypal-tokens-belong-to-me.html) by Antonio Sanso
- [How I made LastPass give me all your passwords](https://labs.detectify.com/2016/07/27/how-i-made-lastpass-give-me-all-your-passwords/) by Mathias Karlsson
- [Hacking Slack using postMessage and WebSocket-reconnect to steal your precious token](https://labs.detectify.com/2017/02/28/hacking-slack-using-postmessage-and-websocket-reconnect-to-steal-your-precious-token/) by Frans Rosén
- [Hacking OAuth2.0 For Fun And Profit](https://drive.google.com/file/d/1Qw3hhValdRAWNGJtLbbFYfKtaevkw4fQ/view) by Pranav Hivarekar
- [Oauth 2.0 redirection bypass cheat sheet](http://nbsriharsha.blogspot.com/2016/04/oauth-20-redirection-bypass-cheat-sheet.html) by nbsriharsha

### Business Logic Flaw

- [Facebook - bypass ads account's roles vulnerability 2015](https://blog.darabi.me/2015/03/facebook-bypass-ads-account-roles.html) by POUYA DARABI
- [How I Could Steal Money from Instagram, Google and Microsoft](https://www.arneswinnen.net/2016/07/how-i-could-steal-money-from-instagram-google-and-microsoft/) by Arne Swinnen
- [Abusing Multistage Logic Flaw to Buy Anything for Free at hk.deals.yahoo.com](http://web.archive.org/web/20161024050917/http://ngailong.com/abusing-multistage-logic-flaw-to-buy-anything-for-free-at-hk-deals-yahoo-com/) by Ron Chan
- [How anyone could have used Uber to ride for free](http://www.anandpraka.sh/2017/03/how-anyone-could-have-used-uber-to-ride.html) by Anand Prakash

### HTTP Header Injection
- [Twitter Overflow Trilogy in Twitter](https://blog.innerht.ml/overflow-trilogy/) by filedescriptor
- [Twitter CRLF](https://blog.innerht.ml/twitter-crlf-injection/) by filedescriptor
- [Adblock Plus and (a little) more in Google](https://adblockplus.org/blog/finding-security-issues-in-a-website-or-how-to-get-paid-by-google)
- [$10k host header](https://sites.google.com/site/testsitehacking/10k-host-header) by Ezequiel Pereira

### Subdomain Takeover

- [Hijacking tons of Instapage expired users Domains & Subdomains](http://www.geekboy.ninja/blog/hijacking-tons-of-instapage-expired-users-domains-subdomains/) by geekboy
- [Reading Emails in Uber Subdomains](https://hackerone.com/reports/156536)
- [Slack Bug Journey](http://secalert.net/slack-security-bug-bounty.html) - by David Vieira-Kurz
- [Subdomain takeover and chain it to perform authentication bypass](https://www.arneswinnen.net/2017/06/authentication-bypass-on-ubers-sso-via-subdomain-takeover/) by Arne Swinnen
- [Hacker.One Subdomain Takeover](https://hackerone.com/reports/159156) - by geekboy

### Email Related

- [This domain is my domain - G Suite A record vulnerability](http://blog.pentestnepal.tech/post/156959105292/this-domain-is-my-domain-g-suite-a-record)
- [I got emails - G Suite Vulnerability](http://blog.pentestnepal.tech/post/156707088037/i-got-emails-g-suite-vulnerability)
- [How I snooped into your private Slack messages [Slack Bug bounty worth $2,500]](http://blog.pentestnepal.tech/post/150381068912/how-i-snooped-into-your-private-slack-messages)
- [Reading Uber’s Internal Emails [Uber Bug Bounty report worth $10,000]](http://blog.pentestnepal.tech/post/149985438982/reading-ubers-internal-emails-uber-bug-bounty)
- [Slack Yammer Takeover by using TicketTrick](https://medium.com/@intideceukelaire/how-i-hacked-hundreds-of-companies-through-their-helpdesk-b7680ddc2d4c) by Inti De Ceukelaire
- [How I could have mass uploaded from every Flickr account!](https://ret2got.wordpress.com/2017/10/05/how-i-could-have-mass-uploaded-from-every-flickr-account/)

### Local File Inclusion

- [Disclosure Local File Inclusion by Symlink](https://hackerone.com/reports/213558)
- [Facebook Symlink Local File Inclusion](http://josipfranjkovic.blogspot.hk/2014/12/reading-local-files-from-facebooks.html)
- [Gitlab Symlink Local File Inclusion](https://hackerone.com/reports/158330)
- [Gitlab Symlink Local File Inclusion Part II](https://hackerone.com/reports/178152)
- [Multiple Company LFI](http://panchocosil.blogspot.sg/2017/05/one-cloud-based-local-file-inclusion.html)
- [LFI by video conversion, excited about this trick!](https://hackerone.com/reports/226756)

### Unrestricted File Upload
- [File Upload XSS in image uploading of App in mopub](https://hackerone.com/reports/97672) by vijay kumar 
- [RCE deal to tricky file upload](https://www.secgeek.net/bookfresh-vulnerability/) by secgeek
- [File Upload XSS in image uploading of App in mopub in Twitter](https://hackerone.com/reports/97672) by vijay kumar (vijay_kumar1110)

### Brute Force
- [Web Authentication Endpoint Credentials Brute-Force Vulnerability](https://hackerone.com/reports/127844) by Arne Swinnen
- [InstaBrute: Two Ways to Brute-force Instagram Account Credentials](https://www.arneswinnen.net/2016/05/instabrute-two-ways-to-brute-force-instagram-account-credentials/) by Arne Swinnen
- [How I Could Compromise 4% (Locked) Instagram Accounts](https://www.arneswinnen.net/2016/03/how-i-could-compromise-4-locked-instagram-accounts/) by Arne Swinnen
- [Possibility to brute force invite codes in riders.uber.com](https://hackerone.com/reports/125505) by r0t
- [Brute-Forcing invite codes in partners.uber.com](https://hackerone.com/reports/144616) by Efkan Gökbaş (mefkan)
- [How I could have hacked all Facebook accounts](http://www.anandpraka.sh/2016/03/how-i-could-have-hacked-your-facebook.html) by Anand Prakash
- [Facebook Account Take Over by using SMS verification code, not accessible by now, may get update from author later](http://arunsureshkumar.me/index.php/2016/04/24/facebook-account-take-over/) by Arun Sureshkumar

### Race Condition

- [Race conditions on Facebook, DigitalOcean and others (fixed)](http://josipfranjkovic.blogspot.hk/2015/04/race-conditions-on-facebook.html) by Josip Franjković
- [Hacking Starbuck for unlimited money](https://sakurity.com/blog/2015/05/21/starbucks.html) by Egor Homakov
- [Race Conditions on Web](https://www.josipfranjkovic.com/blog/race-conditions-on-web) by JOSIP FRANJKOVIĆ
- [Manipulation of ETH balance](https://www.vicompany.nl/magazine/from-christmas-present-in-the-blockchain-to-massive-bug-bounty) by Jesse Lakerveld

### SQL Injection
- [Yahoo – Root Access SQL Injection – tw.yahoo.com](http://buer.haus/2015/01/15/yahoo-root-access-sql-injection-tw-yahoo-com/) by Brett Buerhaus
- [GitHub Enterprise SQL Injection](http://blog.orange.tw/2017/01/bug-bounty-github-enterprise-sql-injection.html) by Orange
- [Yahoo SQL Injection to Remote Code Exection to Root Privilege](http://www.sec-down.com/wordpress/?p=494) by Ebrahim Hegazy
- [Blind SQL Injection in er..I'm not sure what's the DBMS is](http://c0rni3sm.blogspot.com/2017/03/blind-sql-injection-in-erim-not-sure.html) by c0rni3sm

### Remote Code Execution
- [Command Injection in Google Console](http://www.pranav-venkat.com/2016/03/command-injection-which-got-me-6000.html) by Venkat S
- [JDWP Remote Code Execution in PayPal](https://www.vulnerability-lab.com/get_content.php?id=1474) by Milan A Solanki
- [XXE in OpenID: one bug to rule them all, or how I found a Remote Code Execution flaw affecting Facebook's servers](http://www.ubercomp.com/posts/2014-01-16_facebook_remote_code_execution) by Reginaldo Silva
- [How I Hacked Facebook, and Found Someone's Backdoor Script](http://devco.re/blog/2016/04/21/how-I-hacked-facebook-and-found-someones-backdoor-script-eng-ver/) by Orange Tsai
- [How I Chained 4 vulnerabilities on GitHub Enterprise, From SSRF Execution Chain to RCE!](http://blog.orange.tw/2017/07/how-i-chained-4-vulnerabilities-on.html) by Orange Tsai
- [uber.com may RCE by Flask Jinja2 Template Injection](https://hackerone.com/reports/125980) by Orange Tsai
- [Yahoo Bug Bounty - *.login.yahoo.com Remote Code Execution](http://blog.orange.tw/2013/11/yahoo-bug-bounty-part-2-loginyahoocom.html) by Orange Tsai (Sorry its in Chinese Only)
- [How we broke PHP, hacked Pornhub and earned $20,000](https://www.evonide.com/how-we-broke-php-hacked-pornhub-and-earned-20000-dollar/) by Ruslan Habalov
  - *Alert*, God-like Write-up, make sure you know what is ROP before clicking, which I don't =(
- [RCE deal to tricky file upload](https://www.secgeek.net/bookfresh-vulnerability/) by secgeek
- [WordPress SOME bug in plupload.flash.swf leading to RCE in Automatic](https://hackerone.com/reports/134738) by Cure53 (cure53)
- [Read-Only user can execute arbitraty shell commands on AirOS](https://hackerone.com/reports/128750) by 93c08539 (93c08539)
- [Remote Code Execution by impage upload!](https://hackerone.com/reports/158148) by Raz0r (ru_raz0r)
- [Popping a shell on the Oculus developer portal](https://bitquark.co.uk/blog/2014/08/31/popping_a_shell_on_the_oculus_developer_portal) by Bitquark
- [Crazy! PornHub RCE AGAIN!!! How I hacked Pornhub for fun and profit - 10,000$](https://5haked.blogspot.sg/) by 5haked
- [PayPal Node.js code injection (RCE)](http://artsploit.blogspot.hk/2016/08/pprce2.html) by Michael Stepankin
- [eBay PHP Parameter Injection lead to RCE](http://secalert.net/#ebay-rce-ccs)
- [Yahoo Acqusition RCE](https://seanmelia.files.wordpress.com/2016/02/yahoo-remote-code-execution-cms1.pdf)
- [Command Injection Vulnerability in Hostinger](http://elladodelnovato.blogspot.hk/2017/02/command-injection-vulnerability-in.html?spref=tw&m=1) by @alberto__segura
- [RCE in Airbnb by Ruby Injection](http://buer.haus/2017/03/13/airbnb-ruby-on-rails-string-interpolation-led-to-remote-code-execution/) by buerRCE
- [RCE in Imgur by Command Line](https://hackerone.com/reports/212696)
- [RCE in git.imgur.com by abusing out dated software](https://hackerone.com/reports/206227) by Orange Tsai
- [RCE in Disclosure](https://hackerone.com/reports/213558)
- [Remote Code Execution by struct2 Yahoo Server](https://medium.com/@th3g3nt3l/how-i-got-5500-from-yahoo-for-rce-92fffb7145e6)
- [Command Injection in Yahoo Acquisition](http://samcurry.net/how-i-couldve-taken-over-the-production-server-of-a-yahoo-acquisition-through-command-injection/)
- [Paypal RCE](http://blog.pentestbegins.com/2017/07/21/hacking-into-paypal-server-remote-code-execution-2017/)
- [$50k RCE in JetBrains IDE](http://blog.saynotolinux.com/blog/2016/08/15/jetbrains-ide-remote-code-execution-and-local-file-disclosure-vulnerability-analysis/)
- [$20k RCE in Jenkin Instance](http://nahamsec.com/secure-your-jenkins-instance-or-hackers-will-force-you-to/) by @nahamsec
- [Yahoo! RCE via Spring Engine SSTI](https://hawkinsecurity.com/2017/12/13/rce-via-spring-engine-ssti/)
- [Telekom.de Remote Command Execution!](http://www.sec-down.com/wordpress/?p=581) by Ebrahim Hegazy
- [Magento Remote Code Execution Vulnerability!](http://www.sec-down.com/wordpress/?p=578) by Ebrahim Hegazy
- [Yahoo! Remote Command Execution Vulnerability](http://www.sec-down.com/wordpress/?p=87) by Ebrahim Hegazy
- [Pentest: 0day in iTop 2.4.0 gave me Domain Admin Priviledges](https://httpsonly.blogspot.com/2018/04/pentest-0day-in-itop-240-gave-me-domain.html) by httpsonly
- [Airbnb – Ruby on Rails String Interpolation led to Remote Code Execution](https://buer.haus/2017/03/13/airbnb-ruby-on-rails-string-interpolation-led-to-remote-code-execution/) by Brett Buerhaus

####  Deserialization
  - [Java Deserialization in manager.paypal.com](http://artsploit.blogspot.hk/2016/01/paypal-rce.html) by Michael Stepankin
  - [Instagram's Million Dollar Bug](http://www.exfiltrated.com/research-Instagram-RCE.php) by Wesley Wineberg 
  - [(Ruby Cookie Deserialization RCE on facebooksearch.algolia.com](https://hackerone.com/reports/134321) by Michiel Prins (michiel)
  - [Java deserialization](https://seanmelia.wordpress.com/2016/07/22/exploiting-java-deserialization-via-jboss/) by meals

####  Image Tragick
  - [Exploiting ImageMagick to get RCE on Polyvore (Yahoo Acquisition)](http://nahamsec.com/exploiting-imagemagick-on-yahoo/) by NaHamSec
  - [Exploting ImageMagick to get RCE on HackerOne](https://hackerone.com/reports/135072) by c666a323be94d57
  - [Trello bug bounty: Access server's files using ImageTragick](https://hethical.io/trello-bug-bounty-access-servers-files-using-imagetragick/) by Florian Courtial 
  - [40k fb rce](4lemon.ru/2017-01-17_facebook_imagetragick_remote_code_execution.html)
  - [Yahoo Bleed 1](https://scarybeastsecurity.blogspot.hk/2017/05/bleed-continues-18-byte-file-14k-bounty.html)
  - [Yahoo Bleed 2](https://scarybeastsecurity.blogspot.hk/2017/05/bleed-more-powerful-dumping-yahoo.html)

### Money Stealing

- [Round error issue -> produce money for free in Bitcoin Site](https://hackerone.com/reports/176461) by 4lemon

### Miscellaneous

- [SAML Pen Test Good Paper](http://research.aurainfosec.io/bypassing-saml20-SSO/)
- [A list of FB writeup collected by phwd](https://www.facebook.com/notes/phwd/facebook-bug-bounties/707217202701640) by phwd
- [NoSQL Injection](http://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html) by websecurify
- [CORS in action](http://www.geekboy.ninja/blog/exploiting-misconfigured-cors-cross-origin-resource-sharing/)
- [CORS in Fb messenger](http://www.cynet.com/blog-facebook-originull/)
- [Web App Methodologies](https://blog.zsec.uk/ltr101-method-to-madness/)
- [XXE Cheatsheet](https://www.silentrobots.com/blog/2015/12/14/xe-cheatsheet-update/)
- [The road to hell is paved with SAML Assertions, Microsoft Vulnerability](http://www.economyofmechanism.com/office365-authbypass.html#office365-authbypass)
- [Study this if you like to learn Mongo SQL Injection](https://cirw.in/blog/hash-injection) by cirw
- [Mongo DB Injection again](http://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html) by websecrify
- [w3af speech about modern vulnerability](https://www.youtube.com/watch?v=GNU0_Uzyvl0) by w3af
- [Web cache attack that lead to account takeover](http://omergil.blogspot.co.il/2017/02/web-cache-deception-attack.html)
- [A talk to teach you how to use SAML Raider](https://www.usenix.org/conference/usenixsecurity12/technical-sessions/presentation/somorovsky)
- [XSS Checklist when you have no idea how to exploit the bug](http://d3adend.org/xss/ghettoBypass)
- [CTF write up, Great for Bug Bounty](https://ctftime.org/writeups?tags=web200&hidden-tags=web%2cweb100%2cweb200)
- [It turns out every site uses jquery mobile with Open Redirect is vulnerable to XSS](http://sirdarckcat.blogspot.com/2017/02/unpatched-0day-jquery-mobile-xss.html) by sirdarckcat
- [Bypass CSP by using google-analytics](https://hackerone.com/reports/199779)
- [Payment Issue with Paypal](https://hackerone.com/reports/219215)
- [Browser Exploitation in Chinese](http://paper.seebug.org/)
- [XSS bypass filter](https://t.co/0Kpzo52ycb)
- [Markup Impropose Sanitization](https://github.com/ChALkeR/notes/blob/master/Improper-markup-sanitization.md)
- [Breaking XSS mitigations via Script Gadget](https://www.blackhat.com/docs/us-17/thursday/us-17-Lekies-Dont-Trust-The-DOM-Bypassing-XSS-Mitigations-Via-Script-Gadgets.pdf)
- [X41 Browser Security White Paper](https://browser-security.x41-dsec.de/X41-Browser-Security-White-Paper.pdf)
- [Bug Bounty Cheatsheets](https://github.com/EdOverflow/bugbounty-cheatsheet) By EdOverflow
- [Messing with the Google Buganizer System for $15,600 in Bounties](https://medium.freecodecamp.org/messing-with-the-google-buganizer-system-for-15-600-in-bounties-58f86cc9f9a5)
- [Electron Security White Paper](https://www.blackhat.com/docs/us-17/thursday/us-17-Carettoni-Electronegativity-A-Study-Of-Electron-Security-wp.pdf)
- [Twitter's Vine Source code dump - $10080](https://avicoder.me/2016/07/22/Twitter-Vine-Source-code-dump/)
- [SAML Bible](https://blog.netspi.com/attacking-sso-common-saml-vulnerabilities-ways-find/)
- [Bypassing Google’s authentication to access their Internal Admin panels — Vishnu Prasad P G](https://medium.com/bugbountywriteup/bypassing-googles-fix-to-access-their-internal-admin-panels-12acd3d821e3)
- [Smart Contract Vulnerabilities](http://www.dasp.co/)

### Exclusive Bugbounty Writeup Blog
- [Facebook Bugbounty Writeup Blog](https://philippeharewood.com) by philippeharewood

### Interesting but Seems Not Applicable Now
- [RPO that lead to information leakage in Google](http://blog.innerht.ml/rpo-gadgets/) by filedescriptor
- [IE & Edge URL Parsing Problem](https://labs.detectify.com/2016/10/24/combining-host-header-injection-and-lax-host-parsing-serving-malicious-data/) - by detectify
- [xss in Google by IE Weird Behavior](http://blog.bentkowski.info/2015/04/xss-via-host-header-cse.html)
- [Internet Explorer Has a URL Parsing Problem](https://blog.innerht.ml/internet-explorer-has-a-url-problem/) by Jigsaw
- [XSS by Tossing Cookies in Microsoft and Twitter](http://blog.wesecureapp.com/xss-by-tossing-cookies/) by Akhil Reni
- [How I could Steal Your Google Bug Hunter Account with Two Clicks in IE](https://ngailong.wordpress.com/2017/08/07/how-i-could-steal-your-google-bug-hunter-account-with-two-clicks-in-ie/) by Ron Chan
