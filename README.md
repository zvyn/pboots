pboots
======

pboots is a Django project to provide a dynamic web service for booting clients
over the network. It currently supports PXELINUX for booting computers
depending on their IP-address and the current time. This repository is mainly
an draft for one possible way to use the
[pboots/pxelinux](https://github.com/pboots-pxelinux) app.

set it up
---------

I assume you have a working PXELINUX (version >= 6) setup on the same server
running this web service (that is not necessary at all, just makes this how-to
a bit easier) and set DHCP-option 209 to
`http://your-boot-server-IP/pxelinux.cfg/`.

### testing

You don't need to set up a hole server-environment to test this, just
`cp sample-configs/pboots_locale_settings.py pboots/locale_settings.py`, open
it, set a paths for an sqlite-file and enter a hostname and a secret key (any
random combination of ASCII-chars).
You can now run `puthon manage.py syncdb` to set up the databases and a
superuser (you will need it later so say `yes` here).
After a `python manage.py runserver 80` you can configure your test-setup by
going to [http://your-boot-server-ip/cfg](http://localhost/cfg) according to
the instructions in [pboots/pxelinux/README.md](/pboots/pxelinux/README.md).
Note that the page looks ugly only in testing mode since the img and css files
for Django-admin are missing.

### deploying

Just take a look on the files in sample-configs, you should get the idea.
