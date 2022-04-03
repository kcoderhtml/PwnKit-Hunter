<p align="center">
  <img src="https://github.com/Hechtov/Photos/blob/master/PwnKit-Hunter/PwnKit-Hunter%20logo1.png">
</p>
  
# Background

Last week, a significant vulnerability in polkit’s pkexec was publicly disclosed ([link](https://blog.qualys.com/vulnerabilities-threat-research/2022/01/25/pwnkit-local-privilege-escalation-vulnerability-discovered-in-polkits-pkexec-cve-2021-4034)). By exploiting this vulnerability, attackers on a vulnerable host could easily gain full root privileges from any unprivileged user.

Following the public disclosure of this “PwnKit” vulnerability, we developed simple scripts to detect and check if a scanned host is vulnerable or not. The script can help organizations and security teams in their important task of checking all their Linux-based machines and make sure they are not exposed to the Polkit vulnerability.

Additional details can be found in our blog post:  
https://www.cyberark.com/resources/threat-research-blog/checking-for-vulnerable-systems-for-cve-2021-4034-with-pwnkit-hunter


# What is “PwnKit-Hunter” and how it can help me?

PwnKit-Hunter is a set of tools that will search for you whether your system’s polkit package is vulnerable to CVE-2021-4043, a.k.a. PwnKit.
  
The tools are:
  
### CVE-2021-4034_Finder.py:

This script uses your apt cache to find the current installed version of polkit and compare it to the patched version according to your distribution.

### PwnKit-Patch-Finder.c:

The patch of Debian and Ubuntu to CVE-2021-4043 contained new exit() line that occurs only if the policykit-1 package is patched. This code will try to trigger this exit(), and will search for the appropriate code. In case pkexec exited with different code, the package needs to be updated.

DISCLAIMER: This script is only working on Debian and Ubuntu variants, as other distros patched the code in a different way.


# How to run “PwnKit-Hunter”

**CVE-2021-4034_Finder.py:**

```
git clone https://github.com/cyberark/PwnKit-Hunter.git

cd PwnKit-Hunter

chmod +x CVE-2021-4034_Finder.py

./CVE-2021-4034_Finder.py
```
  
**PwnKit-Patch-Finder.c:**

```
git clone https://github.com/cyberark/PwnKit-Hunter.git

cd PwnKit-Hunter

gcc PwnKit-Patch-Finder.c -o PwnKit-Patch-Finder

./PwnKit-Patch-Finder
```
  
# Final Notes
PwnKit-Hunter was developed by CyberArk Labs as a "quick and dirty" POC intended to help security teams worldwide.  

### License:
Copyright (c) 2021 CyberArk Software Ltd. All rights reserved.    
This repository is licensed under MIT License.  
    
### Contributed by:  
Alon Zahavi ([AlonZa](https://www.linkedin.com/in/alon-zahavi-529499143)), Yaniv Yakobovich ([@YanivYakobovich](https://twitter.com/YanivYakobovich)), and Asaf Hecht ([@Hechtov](https://twitter.com/Hechtov))  
  
### Feedback and comments are welcome!  

