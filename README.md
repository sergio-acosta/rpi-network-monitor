# rpi-network-monitor
A simple System V service/daemon with a simple way to check if the network link is up through a determined interface (in this case wlan0) and if it does not, it uses ifup --force to enable it. 

## Setup
1. Use git clone to retrieve the files
`git clone https://github.com/sergio-acosta/rpi-network-monitor`
2. Create a folder in /opt/ to save the script `network-monitor.sh` and set appropiate permissions
```
mkdir /opt/network-monitor
cp network-monitor.sh /opt/network-monitor/network-monitor.sh
chmod 755 /opt/network-monitor/network-monitor.sh
```
3. Create the System V service
```
mv network-monitor /etc/init.d/network-monitor
update-rc.d network-monitor defaults
```
4. Start it and check status
```
service network-monitor start
service network-monitor status
```

## Improvements
If you need to have a log of re-connections attempts just use `logger` to `/var/log/messages` or even better, create your own custom log file.

## Disclaimer
There are probably better ways to do this, just this is the one I came up with at the time. I was using it for a while and worked just fine.

