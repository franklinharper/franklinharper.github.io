---
layout: post
title: 'Migration to new Linux machine'
---

This post will cover the steps required on desktop Linux to migrate to a new hardware configuration.\r\n\r\nIt is assumed that all user data is in the ~/ directory (i.e. user's home directory).\r\n\r\nMigration Steps\r\n-----------------------\r\n\r\n1. Install, configure, test *OS* on New machine.\r\n1. Install, configure, test *applications* on New machine.\r\n1. Stop updating files on Old machine and backup user's home directory to external hard-drive. It is probably best to do this at night since the backup can take quite a while.\r\n    * tar cpf /media/external-drive/home-dir-backup.tar ~/\r\n\r\n    gzip compression can be used if necessary \r\n    * tar cpzf /media/external-drive/home-dir-backup.tgz ~/\r\n1. On New machine restore user's home directory from external harddrive\r\n    * tar -xpf /media/external-drive/home-dir-backup.tar -C ~/\r\n1. Perform final configuration on New machine now that user data has been migrated.
