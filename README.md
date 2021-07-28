# nagios-plugins-fail2ban - a Nagios plugin, reporting the state of fail2ban

I ripped this code from [https://github.com/fail2ban/fail2ban/tree/0.11/files/nagios](https://github.com/fail2ban/fail2ban/tree/0.11/files/nagios)
(it's GPL v2)
That code didn't suit me, because the README suggested you should run the entire script as sudo.
I wasn't prepared to go that far.  It's just not safe.

I took a more nuanced approach, running only the 'fail2ban-client' via sudo, so that if someone 
compromises /usr/lib64/nagios/plugins/check_fail2ban, we're not giving away the whole machine. 

This explicitly includes a file, "fail2ban-nagios", designed to slot into /etc/sudoers.d, allowing 
the nagios userid to run the "fail2ban-client" executable with only the specific parameters
needed for this action. I added the ability to unban addresses from the 'sshd' jail, as we
ran into an operational problem with this.

? Should I submit this back to the original maintainers?  Probably.
