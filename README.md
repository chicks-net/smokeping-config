smokeping-config
================

smokeping config is our derivation of the debian/ubuntu stock smokeping configuration
into something we find easier to use as a base for our installs.

Installation process
--------------------

These instructions assume that you are putting this repo into `/home/chicks/Documents/git/smokeping-config`
which is probably not what you want.
These commands have been translated into an [ansible role](https://github.com/chicks-net/fini-ansible/tree/master/roles/app_smokeping).

In Debian/Ubuntu-land this should do it:

1. `apt-get install apache2 apache2-doc apache2-utils` # should be done before smokeping 
1. `apt-get install smokeping` 
1. `service smokeping stop`
1. `mkdir -p /home/chicks/Documents/git`
1. `cd /home/chicks/Documents/git`
1. `git clone git@github.com:chicks-net/smokeping-config.git`
1. `cd smokeping-config`
1. `touch smokeping_secrets ; chmod 600 smokeping_secrets`
1. `cd /etc/`
1. `mv smokeping smokeping.as_installed`
1. `ln -s ~chicks/Documents/git/smokeping-config smokeping`
1. `service smokeping start`
1. `cd /etc/apache2/conf-available`
1. `ln -s ../../smokeping/apache2.conf smokeping.conf`
1. `a2enconf smokeping`
1. `a2enmod cgid`
1. `service apache2 restart`

After 5-10 minutes you should have graphs in http://localhost/smokeping/smokeping.cgi and making
this available more widely is left as an exercise for the reader.  (Document pull requests are still
welcomed.)

Categories
----------

* Search
* Social
* Gaming
* APAC
* Europe
* DNS
* FINI
* RTB - real time bidding

Thanks
------

* [wikipedia](http://en.wikipedia.org/wiki/List_of_most_popular_websites) provided a nice list of popular
sites with Alexa and Google together rankings.

* [Netcraft](http://toolbar.netcraft.com/stats/topsites) made it easier to find the European sites.

* ["junkken" on askUbuntu.com](http://askubuntu.com/questions/365088/smokeping-web-front-end-on-ubuntu-13-10)
made it clear how to get it workig with Ubuntu's (?Debian's) unique apache2 config system.
