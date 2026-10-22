---
layout: post
title: 'Home data backup recipe'
---

Ok, I've finally decided to get off my butt and do something about making backups of all the precious family data. Up until now it has just been waiting to fall into a digital black hole.

### Ingredients
* one linux server
* enough hard disk space to make backups
* family PCs running Windows that have precious data on them
* a home network
* General information about using snapshot/rsync backup method
* [snapback2 backup software](http://www.perusion.com/misc/Snapback2/snapback2.html)

From here on, I'll suppose that the server, windows PCs and network are already installed.

To get a working backup system, do the following

* Install Config::ApacheFormat from CPAN

            perl -MCPAN -e shell
            cpan> install Config::ApacheFormat
* Install snapback2
* Create /etc/snapback2.conf containing something like this with a Directory directive for each PC

            Hourlies 4
            Dailies 7
            Weeklies 4
            Monthlies 12
            #AutoTime Yes
            AutoTime No
            Compress No
            Debug 4

            #AdminEmail backups@yourdomain.org
            AdminEmail you@yourdomain
            AlwaysEmail Yes

            LogFile /var/log/snapback.log
            ChargeFile /var/log/snapback.charges

            Exclude core.*

            SnapbackRoot /etc/snapback

            #DestinationList /mnt/backup1 /mnt/backup2
            DestinationList /root/snapshot

            RsyncShell none
            Directory /mnt/FranksDocs/
            Directory /mnt/JonsDocs/
            Directory /home/share/

* Run snapback2 from cron every hour

          0 * * * * /usr/bin/snapback2
* Configure PCs to share documents read only
* Use automount and Samba to access the documents on the PC hard disks
    * Put the following into /etc/auto.master

            /mnt file:/etc/auto.mnt
      * For each PC add something like this into /etc/auto.mnt

            + FranksDocs -fstype=smbfs,username=guest,password=,ro,fmask=755,dmask=755 ://192.168.0.4/FranksDocs
    * make sure automount is started at boot time (symbolic link in /etc/rc5.d)
    * Export backups locally read-only through NFS (/etc/exports)
         * /root/snapshot/localhost/mnt/FranksDocs 127.0.0.1(secure,ro,no_root_squash)
         *execute exportfs -a
    * Mount read-only file system accessible to users (/etc/fstab)
         * 127.0.0.1:/root/snapshot/localhost/mnt/FranksDocs /snapshot/FranksDocs nfs ro,addr=127.0.0.1 0 0
          o create mount point /snapshot/FranksDocs
    * Export using Samba so users can access their backups
          * Create /etc/samba/smb.conf

                + # Global Parameters
                  [global]
                  workgroup = YOURWORKGROUP
                  security = SHARE
                  server string =
                  #printing = CUPS
                  #printcap name = CUPS
                  disable spoolss = Yes
                  #show add printer wizard = No
                  wins support = yes
                + [SaveFrank]
                  comment = Recover old versions of Frank's files here
                  path = /snapshot/FranksDocs
                  read only = Yes
                  force user = share
                  force group = family
                  guest ok = Yes
                  nt acl support = No
* That's it you're done
