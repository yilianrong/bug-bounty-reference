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
  - Finding the AngularJS version by executing `angular.verion` in the console.
  - The difference between "Remember me" and "Remember the password" (the author found code decrypting passwords on clint side) when signing in.
  - The payload in this writeup is worth to study and explore.
- [Angular 1.6 - Expression Sandbox Removal](https://blog.angularjs.org/2016/09/angular-16-expression-sandbox-removal.html) by Pete Bacon Darwin
  - What is the expression sandbox, why added the sandbox, why removed the sandbox, what are the security implications.
- [AngularJS 1.6: Life outside the sandbox](https://www.synopsys.com/blogs/software-security/angularjs-1-6-0-sandbox/) by David Johansson
  - A seemed harmless function (orderBy) controlled by attacker could cause large damage than you think.
- [Blind XSS AngularJS Payloads](https://ardern.io/2018/12/07/angularjs-bxss/) by Lewis Ardern
  - There is a list of blind XSS AngularJS payloads.

### JSONP

- [What is JSONP all about](https://stackoverflow.com/questions/2067472/what-is-jsonp-all-about/2067584) by stackoverflow
