# Kernel Pools

The operating system needs a way of managing objects that are created in memory. On windows, this is achieved through the use of Kernel Pools and Executive Objects. Windows uses them to track and manage memory objects by creating separate allocation pools, containing their own Executive Object representing a system structures like files, threads, mutants mutexes.
Each kernel component has its own four byte tag, which is used to identify it in memory. 
Each kernel object in memory is defined in the following way:

![image](https://github.com/MikPrus/Digital-Forensics/assets/72823731/6090abef-e68b-4801-a131-87579658e28d)

Each kernel object in memory is in fact a kernel pool with an EXECUTIVE_OBJECT inside of it that defines what it is, additional options, an object header and an object body ( the real content ) ;)

## Dissecting POOL_HEADER

The POOL_HEADER element is the object that contains the special four byte tag mentioned above. Using volatility we can dissect the POOL_HEADER to find that it is contained within the PoolTag element:

![image](https://github.com/MikPrus/Digital-Forensics/assets/72823731/aa8fe388-72a5-4be8-b1e2-a3a8c334229e)

## If you're interested in how kernel pool are created. Here's how the allocation process looks like when we create a file:

1. > CreateFileA or CreateFileW is called.
    
2. > CreateFileA/W leads to ntdll.dll, that calls the kernel NtCreateFile function.
    
3. > NtCreateFile calls ObCreateObject to request a new File object type.
    
4. > ObCreateObject evaluates the size of the _FILE_OBJECT ( executive object for files ), including space for headers.
    
5. > ObCreateObject finds the _OBJECT_TYPE structure for File objects. Then it checks which 4 byte tag to use and if its better to allocated using paged or non-paged memory.
    
6. > ExAllocatePoolWithTag is called with the arguments defining the size, memory type, and tag of the allocation.
