---
layout: post
title: 'Website Configuration Checklist'
---

This is a short checklist to get a new website up and running ASAP. It is intended for people who know what they're doing and just want a checklist to remember the steps involved and to avoid [a trap when configuring forwarding for Google Apps email addresses](#emailforwarding).

### Pre-requisites
* A Linux server with Apache2 installed
* Root access to configure and restart Apache

### Results
* DNS configured for mydomain.com and www.mydomain.com
* Email accounts configured
* Apache ready to serve requests for mydomain.com and www.mydomain.com

### Steps
1. Register domain name mydomain.com
1. Configure DNS A records for www.mydomain.com and mydomain.com
1. Configure an Apache virtual host to serve www.mydomain.com

        su
        cp /etc/apache2/sites-available/www.existingdomain.com 
            /etc/apache2/sites-available/www.mydomain.com
        make necessary changes in /etc/apache2/sites-available/www.mydomain.com
        a2ensite www.mydomain.com
        mkdir /var/www/www.mydomain.com
        chown user:group /var/www/www.mydomain.com
        /etc/init.d/apache2 restart
1. Create redirect from mydomain.com to www.mydomain.com

        su
        cd /etc/apache2/sites-enabled/
        create ../sites-available/mydomain.com containing  
            RewriteEngine ON  
            RewriteRule ^(.*)$ http://www.mydomain.com/$1 [R=301,L]
        cd /etc/apache2/sites-enabled;ln -s ../sites-available/mydomain.com 
            ./YYY-mydomain.com
        /etc/init.d/apache2 restart
1. Configure Google Apps for mydomain.com, which is just one click @ name.com
1.Create Google Apps admin account
1. Configure email addresses for mydomain.com
    1. <span id="emailforwarding">Configure Admin account forwarding</span>
        1. Log in to Gmail using the account which will be forwarded.
        1. Configure forwarding address in Settings/Forwarding.
        1. Enable forwarding address
        1. **Test forwarding address from a non Gmail account!**
    1. Repeat process for other accounts if necessary, using email nicknames 
         to avoid creating extra accounts.
1. Get started creating some content in /var/www/www.mydomain.com!
