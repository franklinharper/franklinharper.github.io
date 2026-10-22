---
layout: post
title: 'Ubuntu 8.04 Hardy Heron: Automatic login'
---

Of course I don't generally recommend, nor use automatically logging in to your Ubuntu system. But there are some cases in which it can be useful to enable auto logins, such as when a computer user is disabled and can't easily use a keyboard.

So enough talking, it's time for some action!

1. Enable automatic login
 * Log in with account that is authorized as a system administrator
 * Open System/Administration/Login Window
 * In Security tab Enable Automatic Login and choose user
 * If there is a password protected wifi connection, then another password will still be requested by the Gnome Keyring manager.

2. Removing the keyring password :
 * Log in with default account
 * Open Preferences/Encryption and Keyrings
 * Select the entry "login Automatically unlocked when user logs in."
 * Click on "Change Unlock Password"
 * Enter old password, and leave new passwords blank

That's it you're done!
