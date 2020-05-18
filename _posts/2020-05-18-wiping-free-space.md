---
layout: post
title: Wiping Free Space
---

Wiping the free space of a drive is useful when the drive is not encrypted, and you want to make sure deleted files cannot be recovered. Wiping multiple times is mostly useless now, as the original analysis by Peter Gutmann, which found that their expensive equipment can sometimes detect the original value of an overwritten bit, was done on obsolete hardware, whereas modern hard disks are made with much higher densities and tighter tolerances. Filling all empty space with 0s will most likely be enough.

It is important to note that this is not a fault-prove method, as there may still be data left in relocated or bad sectors. Physical destruction or full disk encryption would be the preferred method for better security.

Windows:

```
cipher /w:C:\
```

Linux:

```bash
cat /dev/zero > zero.file
sync
rm zero.file
```
