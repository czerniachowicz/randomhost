
# Random Host

  

Generate and set a random hostname on Linux on each boot.


## Installation

  

### Using systemd
The following should be run as root, or prefixed with `sudo`:

Copy randomhost to /usr/bin/ or another location included in your $PATH variable
`cp randomhost /usr/bin/randomhost`

Make it executable
`chmod +x /usr/bin/randomhost`

Copy randomhost.service to /etc/systemd/system/
`cp randomhost.service /etc/systemd/system/randomhost.service`

Set the randomhost.service permissions to 644 
`chmod 644 /etc/systemd/system/randomhost.service`

Reload systemd
`systemctl daemon-reload`

Enable the service
`systemctl enable randomhost`

Before relying on the boot process, you can manually start the service to ensure it works as expected
`systemctl start randomhost`

Since the script uses `logger` to send messages to syslog, you should be able to track its activities in the system logs. Depending on your system, these might be found in `/var/log/syslog` or accessible via `journalctl`.

Note: you will need to logout and log back in for your current session to display the updated hostname.

### Using init.d

Copy randomhost to /etc/init.d/
`cp randomhost /etc/init.d/randomhost`

Make it executable
`chmod +x /etc/init.d/randomhost`

Create a symbolic link in the runlevel directory
`ln -s /etc/init.d/randomhost /etc/rc.d/rc3.d/S98xrandomhost`

Before relying on the boot process, you can manually execute the service to ensure it works as expected
`/etc/init.d/randomhost`