---
layout: post
title: 'Handling large Bitmaps on Android'
---


- limited memory
-> Exception
-> first approach: Stack overflow solution
-> second approach direct bitmap (without temporary bitmap in memory)
-> compare quality of both approaches
-> analyze source code to see of
second approach handles large bitmaps, first doesn't
usage: camera apps, resizing camera resolution to screen resolution
