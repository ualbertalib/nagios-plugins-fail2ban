I ripped this code from https://github.com/fail2ban/fail2ban/tree/0.11/files/nagios
That code didn't suit me, because the README suggested you should run the entire script as sudo.
I wasn't prepared to go that far.  It's just not safe.

I took a more nuanced approach, running only the 'fail2ban-client' via sudo, so that if someone 
compromises /usr/lib64/nagios/plugins/check_fail2ban, we're not giving away the whole machine. 

This explicitly includes a file, "fail2ban-nagios", designed to slot into /etc/sudoers.d, allowing 
the nagios userid to run the "fail2ban-client" executable with only the specific (query) parameters
needed for this action.  Thus, the nagios userid can't unban an IP address, or perform anything but
'status' actions. 

? Should I submit this back to the original maintainers?  Probably.
