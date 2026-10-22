---
layout: post
title: 'Android BootReceiver not working'
---

Running application code after an Android device has finished booting is pretty straightforward. And there are already a few good tutorials available.

But, all the tutorials that have not been updated after the release of Android 2.2 (API 8), don't mention that for it to work the App must be installed on internal storage.

This restriction on using internal storage only is [documented](http://developer.android.com/guide/appendix/install-location.html), and a good overview is also available on [stackoverflow]( http://stackoverflow.com/questions/2784441/trying-to-start-a-service-on-boot-on-android)
