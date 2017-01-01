# Web Application (In)security

The core security problem facing web applications is that users can supply arbitrary input. 


## The Evolution of Web Applications

In the beginning, web sites were mostly static content. There was no authentication since there was no need. Back then, when a site was compromised, it was mostly server application related. No real sensitive data, so sites were usually defaced or used to distribute their warez. Think blink tags on the epilepsy site back in the early 2000s.


Now, most sites are highly functional web applications.

  * relies on two-way flow between server and browser
  * supports registration and login
  * financial transactions
  * search
  * user created content

### Common Web Application Functions

*Every day external user functions:*
  * shopping
  * social media
  * banking
  * web search
  * auctions
  * gambling
  * blogging
  * email
  * wikis

*Internal business functions:*
  * HR related apps
    * payroll access
    * performance review
    * recruitment
    * disciplinary procedures
  * Admin interfaces
    * web and mail servers
    * user workstations
    * vm admin
  * Collaboration software
    * sharing internal docs
    * managing workflow, projects, issues
  * Software Services
  * Desktop Applications have been migrated to the cloud in many cases

### Benefits of Web Applications
  * HTTP
    * is lightweight and connectionless
    * does not require server to hold open a connection per user
    * allows for secure communication with proxies and tunneling over other protocols
  * Browsers are readily available on both computers and mobile devices
  * Core technologies and languages used to build web apps is relatively simple

### Web Application Security

SSL may defend against eavesdropping, but none of the below.

*Common Categories of Vulnerability*
  * *Broken authentication:* Various defects within the application's login mechanism
  * *Broken access controls:* Application fails to protect access to its data and functionality
  * *SQL injection:* Submitted crafted input that interfere's with application's back-end databases
  * *Cross-site scripting (XSS):* Enables attacker to target other users of the application
  * *Information leakage:* Application reveals sensitive information
  * *Cross-site request forgery: (CSRF):* Application that hijacks a user's session and privilege level and performs unintended actions









