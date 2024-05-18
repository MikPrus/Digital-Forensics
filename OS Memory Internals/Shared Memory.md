# What is Shared Memory?

Shared process memory is an integral part of how the operating systems work. Even though system processes are separated from one another, they can share some memory regions to share data and effectively communicate with eachother.
Additionally, by using this mechanism, the operating system can save a lot of space, because instead of allocating multiple pages in memory for the same thing in different processes, it can just create the shared address space, that can be accesed by every process that needs this specific resource.

# How does it work? 

Shared memory is a memory region with a special flag, indicating that it is shared and therefore can be written and read by different processes, that are normally limited to their own memory space.
