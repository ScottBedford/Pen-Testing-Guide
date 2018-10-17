### Linux BASH Commands

#### Basic Linux Commands
```
updatedb		# Update local database
locate filename		# Locate filename
which filename		# Returns pathname for executable
find / -name sbd*	# Find files matching sbd*
man find		# For find or other manual
passwd			# Change password
su username		# Change user

# Find files with name sbd and execute 'file' command to ascertain file type
find / -name sbd* -exec file {} \;
```

#### Services
```
service ssh start		# Start SSH service
netstant -antp | grep sshd	# Check if SSH is running/stopped
service ssh stop

service apache2 start		# Start HTTP server
http://127.0.0.1		# Check if server running
/var/www/			# Default apache server document root
echo "Some text" > output.html	# Make page in terminal
service apache2 stop	
```

#### Service management
```
/etc/init.d/			# Wrapper for managing services
/etc/init.d/ssh start		# Alternate way to start services
/etc/init.d/ssh stop		# Alternate way to stop services

# Service boot persistence
update-rc.d ssh enable
update-rc.d apache2 enable
```

