---
layout: post
title: 'Compiling log4cpp 1.0 with gcc 4.3 or 4.4'
---

In gcc 4.3 some [bugs were fixed](http://gcc.gnu.org/gcc-4.3/porting_to.html), unfortunately they can cause compile errors with code that would compile with older versions.\r\n\r\nIn particular this is the case with **log4cpp 1.0** which fails with the following message:\r\nBasicLayout.cpp:37:5: error: 'auto_ptr' in namespace 'std' does not name a type\r\n\r\nLuckily the fix is very simple; all that is required to get a clean compile is add an  **#include &lt;memory&gt;** in src/BasicLayout.cpp.\r\n
