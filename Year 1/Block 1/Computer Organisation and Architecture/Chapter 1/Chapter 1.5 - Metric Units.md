---
title: Chapter 1.5 - Metric Units
---
Computer scientists use the following prefixes to denote units:
![[MetricPrefixes.png]]

However, common industry practice for measuring memory, disk, file, and database sizings is to use a power of two. So a Kilobyte would be 2^10 
(1024) rather than 10^3 (1000), a megabyte 2^20 rather than 10^6, etc. Speeds (Such as a 1-Kbps download) use powers of ten. It's a bit of a clusterfuck.

To avoid such ambiguity, there's been a new term introduced for prefixes that use the power of ten; Kibibyte for 2^10 bytes, mebibyte for 2^20 bytes, etc. However these symbols aren't exactly in wide use yet, so when you see KB, assume it is 2^10. (Kibibyte would be KiB)