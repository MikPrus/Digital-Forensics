# What is Shared Memory?

Shared process memory is an integral part of how the operating systems work. Even though system processes are separated from one another, they can share some memory regions to share data and effectively communicate with eachother.
Additionally, by using this mechanism, the operating system can save a lot of space, because instead of allocating multiple pages in memory for the same thing in different processes, it can just create the shared address space, that can be accesed by every process that needs this specific resource.

# How does it work? 

Shared memory is a memory region with a special flag, indicating that it is shared and therefore can be written and read by different processes, that are normally limited to their own memory space.
For example, on Windows shared memory regions are marked with the RWX+S flag and on linux with the MAP_SHARED flag.

# Potential misuse
Shared memory regions can be creatively misused by malware developers, as they allow other processes to access data outside of their memory space.
This can allow for sneaky code injection where no memory in the target is overwritten, because the target process can be tricked to execute shellcode
that resides in the shared memory space.
## Resources:
https://billdemirkapi.me/sharing-is-caring-abusing-shared-sections-for-code-injection/ --> Shared memory code injection
https://www3.physnet.uni-hamburg.de/physnet/Tru64-Unix/HTML/APS33DTE/DOCU_004.HTM --> Linux memory region flag types
