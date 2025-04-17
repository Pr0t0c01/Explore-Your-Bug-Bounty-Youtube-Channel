```
 __          __  _                             __                     
 \ \        / / | |                           / _|                    
  \ \  /\  / /__| | ___ ___  _ __ ___   ___  | |_ _ __ ___  _ __ ___  
   \ \/  \/ / _ \ |/ __/ _ \| '_ ` _ \ / _ \ |  _| '__/ _ \| '_ ` _ \ 
    \  /\  /  __/ | (_| (_) | | | | | |  __/ | | | | | (_) | | | | | |
     \/  \/ \___|_|\___\___/|_| |_| |_|\___| |_| |_|  \___/|_| |_| |_|
                                                                      
                                                                      
  ______            _                 __     __                ____                ____                    _         
 |  ____|          | |                \ \   / /               |  _ \              |  _ \                  | |        
 | |__  __  ___ __ | | ___  _ __ ___   \ \_/ /__  _   _ _ __  | |_) |_   _  __ _  | |_) | ___  _   _ _ __ | |_ _   _ 
 |  __| \ \/ / '_ \| |/ _ \| '__/ _ \   \   / _ \| | | | '__| |  _ <| | | |/ _` | |  _ < / _ \| | | | '_ \| __| | | |
 | |____ >  <| |_) | | (_) | | |  __/    | | (_) | |_| | |    | |_) | |_| | (_| | | |_) | (_) | |_| | | | | |_| |_| |
 |______/_/\_\ .__/|_|\___/|_|  \___|    |_|\___/ \__,_|_|    |____/ \__,_|\__, | |____/ \___/ \__,_|_| |_|\__|\__, |
             | |                                                            __/ |                               __/ |
             |_|                                                           |___/                               |___/ 
```
  
## Django Debug Mode with Nuclei
##### Today Topic will be "How to find Django Debug Mode with Nuclei". 
##### It is easy to find bug. This vulnerability still exists in subdomains of bug bounty sites. I also have found this bug once in an vulnerability disclosure program. Let's Start !

#### Bug Bounty Tips
```
- If you learn a new vulnerability, do research detail, try to understand how it works and imagine scenarios.
- If you found a vulnerability in a target, try to create nuclei template for this and add in your recon. 
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
nuclei -l targets.txt -t <path/nuclei-template>.yaml -o vulnerable-targets.txt
```
