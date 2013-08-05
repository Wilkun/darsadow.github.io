---
layout: post
title: "LAMP for Windows"
date: 2013-08-04 21:46
comments: true
categories: Server
---

I'm a huge fan on *NIX operating sytems. I love console and I can't imagine how to work with git with GUI but when it comes to day-to-day work every Linux Desktop simply sux.

And I'm not talking about how it looks. Every Linux has his thing with stability. For example java - one day it's ok and next day it's broken God knows why. I don't have these problems when I'm on Windows. Everything is simply working. BTW when I'm using Windows 8 my laptop it gives me 4 hours on battery. With Ubuntu only 1,5.

But I'm still webdeveloper so I need server with *NIX and easy access when I need it. The solution is virtualization.

 * I have power of unix console via Putty
 * Code editors are running under Windows, so they are rock solid stable.
 * Files are visible via Samba & Windows Mapped Network Drive W:\ so I'm working like on Windows.
 * I have internal domains and properly configured Apache, so for new project all I need is create a new directory.
 * When I don't need Linux I can simply turn off VM

After some time I've finally created generic VM for PHP/Rails development. AFAIR it's third generation when I'm recreating my dev env. But after some time it's really easy and now packaged before I've imported all stuff inside machine ;)

Contents
--------

 * Ubuntu 13.04 - user: dev, password: root
 * Apache 2.2.22
 * PHP 5.4.9
 * MySQL 5.5.32 - user: root, password: root, accessible from any host
 * PostgreSQL 9.2.4 - nothing changed
 * [RVM][3]
   * Ruby 2 & Rails 4
   * Ruby 1.9.3-p448
 * .gitconfig - lots of aliases for less typing - remember to change user and email settings
 * .bash_aliases - better shell experience and again lots of aliases

Installation
------------

 * [Download package][1]
 * Import it using File -> Import Appliance from VirtualBox main menu
 * Run VM

As I checked network interfaces has changed names. Check how it is in your case

```
ip link show
```

and accordingly change names in /etc/network/interfaces

Last thing - dynamic DNS on Windows side. You need [Acrylic DNS Proxy][2] and first DNS setted to 127.0.0.1. Acrylic offers hosts file with wildcards where you can set all development domains to VM IP.

```
192.168.56.7    *.dev
192.168.56.7    *.local
192.168.56.7    *.etc
```

And the last thing. `/var/www/` is available under `\\192.168.56.7\www`. I suggest you use it as Windows Mapped disk.

Enjoy if you like it / Hate me if I've forgot about something ;)

[1]: https://docs.google.com/file/d/0B2iWs6XKRSHlMXdsckdvVlF4SXM/edit?usp=sharing
[2]: http://sourceforge.net/projects/acrylic/
[3]: https://rvm.io/
