### Wordpress Pen Testing Tips

##### Default upload directory
```
<ip>.com/wp-content/uploads/yearnum/monthnum/filename
```

##### WPScan, enumerate plugins, users, themes
```
wpscan -u http://<ip> --enumerate p --enumerate u --enumerate t
```

