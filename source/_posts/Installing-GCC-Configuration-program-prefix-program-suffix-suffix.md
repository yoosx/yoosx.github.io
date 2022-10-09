---
title: Installing-GCC-Configuration-program-prefix-program-suffix-suffix
date: 2022-10-09 15:03:02
tags:
---

`
--program-prefix=prefix
`
GCC supports some transformations of the names of its programs when installing them. This option prepends prefix to the names of programs to install in bindir (see above). For example, specifying --program-prefix=foo- would result in ‘gcc’ being installed as /usr/local/bin/foo-gcc.

`
--program-suffix=suffix
`  
Appends suffix to the names of programs to install in bindir (see above). For example, specifying --program-suffix=-3.1 would result in ‘gcc’ being installed as /usr/local/bin/gcc-3.1.