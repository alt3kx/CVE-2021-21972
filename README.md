# CVE-2021-21972 (checker)
VMware vCenter Server CVE-2021-21972 Remote Code Execution Vulnerability

This script looks the existence of CVE-2021-21972 based on the following PATH
"/ui/vropspluginui/rest/services/uploadova" trough a POST request and looking in 
response body (500) the words "uploadFile",that means the vCenter is avaiable 
to accept files via POST without any restrictions

Manual inspection: 
``` 
# curl -i -s -k -X $'GET' -H $'Host: <target>' -H $'User-Agent: alex666' $'https://<target>/ui/vropspluginui/rest/services/getstatus'
```

```
# curl -i -s -k -X $'GET' -H $'Host: <target>' -H $'User-Agent: alex666'$'https://<target>/ui/vropspluginui/rest/services/uploadova'
```

```
# curl -i -s -k -X $'POST' -H $'Host: <target>' -H $'User-Agent: alex666' -H $'Content-Type: application/x-www-form-urlencoded' -H $'Content-Length: 0' $'https://<target>/ui/vropspluginui/rest/services/uploadova'

```
# References: 
https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-21972  
https://www.vmware.com/security/advisories/VMSA-2021-0002.html

# Usage
```nmap -p443 --script CVE-2021-21972.nse <target>```

# Output
```
---
-- @usage
-- nmap -p443 --script CVE-2021-21972.nse <target>
-- @output
-- PORT    STATE SERVICE
-- 443/tcp open  https
-- | CVE-2021-21972: 
-- |   VULNERABLE:
-- |   vCenter 6.5-7.0 RCE
-- |     State: VULNERABLE (Exploitable)
-- |     IDs:  CVE:CVE-2021-21972
-- |       The vSphere Client (HTML5) contains a remote code execution vulnerability in a vCenter Server plugin. 
-- |       A malicious actor with network access to port 443 may exploit this issue to execute commands with 
-- |       unrestricted privileges on the underlying operating system that hosts vCenter Server.
-- |     Disclosure date: 2021-02-23
-- |     References:
-- |_      https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-21972
```

![Screen Recording](https://github.com/alt3kx/CVE-2021-21972/blob/main/CVE-2021-21972.gif)

# Author
Alex Hernandez aka <em><a href="https://twitter.com/_alt3kx_" rel="nofollow">(@\_alt3kx\_)</a></em>
