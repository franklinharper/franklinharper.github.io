---
layout: post
title: 'Ubuntu 8.04 Hardy Heron: Automatic login'
---

Of course I don't generally recommend, nor use automatically logging in to your Ubuntu system. But there are some cases in which it can be useful to enable auto logins, such as when a computer user is disabled and can't easily use a keyboard.\r\n\r\nSo enough talking, it's time for some action!\r\n\r\n1. Enable automatic login\r\n * Log in with account that is authorized as a system administrator\r\n * Open System/Administration/Login Window\r\n * In Security tab Enable Automatic Login and choose user\r\n * If there is a password protected wifi connection, then another password will still be requested by the Gnome Keyring manager.\r\n\r\n2. Removing the keyring password :\r\n * Log in with default account\r\n * Open Preferences/Encryption and Keyrings\r\n * Select the entry "login Automatically unlocked when user logs in."\r\n * Click on "Change Unlock Password"\r\n * Enter old password, and leave new passwords blank\r\n\r\nThat's it you're done!
