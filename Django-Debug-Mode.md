## Django Debug Mode with Nuclei

##### Today Topic will be "How to find Django Debug Mode with Nuclei". 
##### It is easy to find bug. This vulnerability still exists in subdomains of bug bounty sites. It can expose sensitive data like database password, unauthenticated access and RCE. I also have found this bug once in an vulnerability disclosure program. Let's Start !

#### Bug Bounty Tips
```
- If you learn a new vulnerability, do research detail, try to understand how it works and imagine scenarios.
- If you found a vulnerability in a target, try to create nuclei template for this and add in your recon. 
```

#### How Django Debug Mode Work?
```
Typically, debug mode enabling is purposed for developer to trace errors while website testing.
When website raise unexpected error, detail information of website status will show in frontend if debug mode is enabled.
So, to detect a django website is enabled debug mode or not, we just need to send error request like 404 not found.
Eg - Target is https://redacted.com/. Request to https://redacted.com/abcd123 via browser.
   - If /abcd123 is not existed in redacted.com, it will show 404 not found.
   - At that time, if debug mode is enable, other confidential information will leak with this error. 
```

#### Dorks
```
Shodan
=======
http.component:django
http.title:"DisallowedHost at /"
http.title:"Django REST framework"
http.html:"Using the URLconf defined"
html:"URLconf defined" 404

Censys
======
443.https.get.body: "URLconf defined"
```
#### Download Script from Shodan Facet
```
var ipElements=document.querySelectorAll('strong');var ips=[];ipElements.forEach(function(e){ips.push(e.innerHTML.replace(/["']/g,''))});var ipsString=ips.join('\n');var a=document.createElement('a');a.href='data:text/plain;charset=utf-8,'+encodeURIComponent(ipsString);a.download='download.txt';document.body.appendChild(a);a.click();
```
#### Nuclei Scanning
```
# My Template URL
https://github.com/Pr0t0c01/Custom-Nuclei-Templates/blob/main/misconfig/debug/django-debug-mode.yaml

nuclei -l targets.txt -t <path/nuclei-template>.yaml -o vulnerable-targets.txt
```
#### Youtube Video
[Will Update Soon](youtube)
