vilain_openbsd
======

Jan Helbling's fork!

Mimic fail2ban with pf for OpenBSD.

Inspired from http://www.vincentdelft.be/post/post_20161106

Installation : 
---------------

Download the repository, then run

	make install

This will put `vilain` script in /usr/local/bin, `vilain.py` in
/usr/local/sbin and add a rc script.

Install python-3.*

	pkg_add python


In pf.conf, add according to your configuration : 

    table <vilain_bruteforce> persist
    block quick from <vilain_bruteforce> 

You might want to add a cron task to remove old banned IP. As example, to ban for one day max : 

    pfctl -t vilain_bruteforce -T expire 86400

To see banned IP : 

    pfctl -t vilain_bruteforce -T show


Run vilain
---------------

Run vilain manually or via rc script : 

	rcctl enable vilain
	rcctl start vilain
