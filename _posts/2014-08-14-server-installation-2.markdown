---
author: tjones
comments: false
date: 2014-08-14 11:33:53+00:00
layout: post
slug: server-installation-2
title: New Server Installation/ New Blogging Engine / Web and Mail on Ubuntu
wordpress_id: 1207
categories:
- old
tags:
- Digital Ocean
- Install Dropbear
- Old
- SSH
- UFW
---

As you have have noticed from some of the recent posts, and the bit of downtime I have done some reconfiguration of this website. I switched the blog engine from wordpress to ghost. I have also switched from Debian to Ubuntu (and made a few other changes). Some details about the new config are as follows. The new setup is based on the ghost image from Digital Ocean (the host of the VPS that this website runs on). I will discuss why I made this change later.

[caption id="attachment_1318" align="alignright" width="226"][![Image Via Flickr (user sylvar) https://flic.kr/p/3M87z](http://www.theojones.name/wp-content/uploads/2014/12/31436961_33399f4066_o-226x300.jpg)](http://www.theojones.name/wp-content/uploads/2014/12/31436961_33399f4066_o.jpg) Image Via Flickr (user sylvar) https://flic.kr/p/3M87z[/caption]

I use the mosh remote connection system rather than Openssh to remotely manage the server. The instructions [available on the Mosh website](http://mosh.mit.edu/) work well for this installation.

Mosh
$ sudo apt-get install python-software-properties

$ sudo add-apt-repository ppa:keithw/mosh

$ sudo apt-get update

$ sudo apt-get install mosh

[Mosh has multiple clear benefits.](http://www.linuxscrew.com/2012/04/11/why-mosh-is-better-than-ssh/) 1) it handles special sequences like control-c better than ssh (i.e it dosn't wait for the current task to finish), 2) it can handle network disconnects and IP address changes, 3)its executable runs as a normal user, minimizing security issues, and 4) it handles lagged terminals better. It is worth noting that Mosh is not a complete replacement for SSH, it still uses SSH for authentication.

Using mosh from the client side is simple.

$mosh root@server

It may be a good idea to swap OpenSSH for the lighter weight dropbear if you don't use Mosh.Install Dropbear

$ apt-get install dropbear

Edit
/etc/default/dropbear

Set _NO_START=0 _
This option makes dropbear run on boot.

Also set _DROPBEAR_EXTRA_ARGS="-a"_.

If you installed dropbear remove the openssh server if it is present.

$ apt-get remove openssh-server

Reboot.

You may want to create a non-root user at this point. This has some security advantages (mostly in the case of multi user systems). You can see some articles on this as follows
[http://security.stackexchange.com/questions/34915/what-is-the-actual-value-of-disabling-remote-root-login-using-ssh](http://security.stackexchange.com/questions/34915/what-is-the-actual-value-of-disabling-remote-root-login-using-ssh)
[https://linuxacademy.com/blog/linux/when-you-should-and-should-not-disable-root-login/](https://linuxacademy.com/blog/linux/when-you-should-and-should-not-disable-root-login/)

It can be done as the following:
useradd theo

I use the UFW firewall. Two good articles on this are as follows.

[https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)
[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-mosh-on-a-vps](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-mosh-on-a-vps)

Here is a summary of what I did.
$apt-get install ufw

The above command installs UFW. This is often installed by defauly

$ ufw allow 22

The above command allows ssh to pass through the firewall.

$ufw allow 60000:61000/udp

The above command allows mosh to pass through.

Edit /etc/default/ufw and adjust ipv6 settings

The following two commands sets all defaults to deny, for both outgoing and incoming traffic
$sudo ufw default deny incoming

$sudo ufw default deny outgoing

Start UFW

sudo ufw disable --- just in case its on
sudo ufw enable

ufw allow out 53

The above allows outgoing DNS traffic

ufw allow http --- web
ufw allow out http
ufw allow https --- web over ssl
ufw allow out https

ufw allow smtp -- to send/receive email
ufw allow out smtp

ufw allow imap -- pick up email

I poked around with an alternate setup for a LEMP Stack. Here are some notes
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-14-04)

apt-get update && apt-get upgrade

apt-get install nginx

apt-get install mysql-server
mysql_install_db
mysql_secure_installation --- run through the wizard

apt-get install php5-fpm php5-mysql

Configure PHP
nano /etc/php5/fpm/php.ini

set
cgi.fix_pathinfo=0

edit /etc/nginx/nginx.conf

under http add
fastcgi_buffers 8 16k;
fastcgi_buffer_size 32k;

Set NGINx config
See notes

Automatic updates
http://www.richud.com/wiki/Ubuntu_Enable_Automatic_Updates
[https://help.ubuntu.com/14.04/serverguide/automatic-updates.html](https://help.ubuntu.com/14.04/serverguide/automatic-updates.html)
apt-get install unattended-upgrades
edit /etc/apt/apt.conf.d/50unattended-upgrades

At the very least enable security updates (should be enabled by default)
uncomment the "${distro_id}:${distro_codename}-updates"; line to enable other updates.

edit /etc/apt/apt.conf.d/10periodic
set
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";

Email
[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-postfix-e-mail-server-with-dovecot](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-postfix-e-mail-server-with-dovecot)
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/mail.key -out /etc/ssl/certs/mailcert.pem
sudo openssl req -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/mail.key -out mailcert.csr

aptitude remove exim4 && aptitude install postfix && postfix stop
Install as internet site and follow wizard (although config will be cleared)
Edit
/etc/postfix/master.cf

set
submission inet n - - - - smtpd
-o syslog_name=postfix/submission
-o smtpd_tls_wrappermode=no
-o smtpd_tls_security_level=encrypt
-o smtpd_sasl_auth_enable=yes
-o smtpd_recipient_restrictions=permit_mynetworks,permit_sasl_authenticated,reject
-o milter_macro_daemon_name=ORIGINATING
-o smtpd_sasl_type=dovecot
-o smtpd_sasl_path=private/auth

wipe main.cf (copy it to a new folder if nesarry)
cp /etc/postfix/main.cf /etc/postfix/main.cf.orig
rm /etc/postfix/main.cf

Set
myhostname = mail.domain.com
myorigin = /etc/mailname
mydestination = mail.domain.com, domain.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
smtpd_tls_cert_file=/etc/ssl/certs/mailcert.pem
smtpd_tls_key_file=/etc/ssl/private/mail.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_security_level=may
smtpd_tls_protocols = !SSLv2, !SSLv3
local_recipient_maps = proxy:unix:passwd.byname $alias_maps

edit /etc/aliases and set the file's content as the following
mailer-daemon: postmaster
postmaster: root
nobody: root
hostmaster: root
usenet: root
news: root
webmaster: root
www: root
ftp: root
abuse: root
root: theo

newaliases

aptitude install dovecot-core dovecot-imapd

clear /etc/dovecot/dovecot.conf
rm /etc/dovecot/dovecot.conf

create /etc/dovecot/dovecot.conf
disable_plaintext_auth = no
mail_privileged_group = mail
mail_location = mbox:~/mail:INBOX=/var/mail/%u
userdb {
driver = passwd
}
passdb {
args = %s
driver = pam
}
protocols = " imap"
protocol imap {
mail_plugins = " autocreate"
}
plugin {
autocreate = Trash
autocreate2 = Sent
autosubscribe = Trash
autosubscribe2 = Sent
}
service auth {
unix_listener /var/spool/postfix/private/auth {
group = postfix
mode = 0660
user = postfix
}
}
ssl=required
ssl_cert =< /etc/ssl/certs/mailcert.pem
ssl_key =< /etc/ssl/private/mail.key

newaliases
postfix start
service dovecot restart

adjusting as nessarry

Useful Tools:
p7zip-full
curl
apt-get install curl libcurl3 libcurl3-dev php5-curl

apt-get install mailutils -- send email from the command line
