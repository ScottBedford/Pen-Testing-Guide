### Linux Tips and Tricks

#### Monitor linux processes without root permissions using pspy. Useful for identifying cron jobs
```
git clone https://github.com/DominicBreuker/pspy.git
cd /opt/pspy
go build

# Transfer pspy to target and run
chmod +x pspy
./pspy
```
#### Find files modified in home last 60 minutes
`find /home -ctime -60`
