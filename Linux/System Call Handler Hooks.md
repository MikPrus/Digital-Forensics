# System Call Handler Hooks

Hooking system calls is one of the most popular way of controlling userland applications.
This technique can be both used on Windows ( although with some restrictions ) and on Linux.
On Windows and on Linux there's a special table with entries containing addresses of system
functions. On Windows, its the SSDT and on Linux is the system call table.
Both of these structures can be overwritten, so that its elements don't point to valid system
calls but to functions introduced by malware.
