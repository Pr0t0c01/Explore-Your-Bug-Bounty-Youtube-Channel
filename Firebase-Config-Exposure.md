## Firebase Config Exposure with Nuclei

##### Today Topic will be "How to find Firebase Config with Nuclei".
##### Generally firebase are only vulnerable when they are misconfigured. Even you found apikey and other data of firebase, it have no impact since they are not sensitive. But you should recon them. If firebase is misconfigured, you can takeover them.
##### Let's Start !

#### Bug Bounty Tips
```
- If you learn a new vulnerability, do research detail, try to understand how it works and imagine scenarios.
- If you found a vulnerability in a target, try to create nuclei template for this and add in your recon.
```

#### Dorks
```
FOFA
=====
(body="firebaseConfig" || body="firebaseapp.com" || body="databaseURL" || body="appspot.com")
```

#### Download
```
You can download result data as csv in FOFA.
```

#### Nuclei Scanning
```
# My Template URL
https://github.com/Pr0t0c01/Custom-Nuclei-Templates/blob/main/misconfig/exposure/firebase-config-exposure.yaml

nuclei -l targets.txt -t <path>/firebase-config-exposure.yaml -o vulnerable-targets.txt
```
#### Youtube Video
[Comming Soon]()
