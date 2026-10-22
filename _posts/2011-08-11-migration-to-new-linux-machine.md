---
layout: post
title: 'Migration to new Linux machine'
---

This post will cover the steps required on desktop Linux to migrate to a new hardware configuration.

It is assumed that all user data is in the ~/ directory (i.e. user's home directory).

Migration Steps
-----------------------

1. Install, configure, test *OS* on New machine.
1. Install, configure, test *applications* on New machine.
1. Stop updating files on Old machine and backup user's home directory to external hard-drive. It is probably best to do this at night since the backup can take quite a while.
    * tar cpf /media/external-drive/home-dir-backup.tar ~/

    gzip compression can be used if necessary 
    * tar cpzf /media/external-drive/home-dir-backup.tgz ~/
1. On New machine restore user's home directory from external harddrive
    * tar -xpf /media/external-drive/home-dir-backup.tar -C ~/
1. Perform final configuration on New machine now that user data has been migrated.
