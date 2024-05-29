# DKOM Attacks

Direct Kernel Object Manipulation attacks work by modifying memory structures like processes to hide malicious code or even whole processes from the eyes of analysts. That can be for example achieved by overwriting the _FLINK and _BLINK structures of _EPROCESS to make the active process list go AROUND the malicious process and miss it or by unlinking DLL's and making Remote DLL Injection harder to spot and verify.
Fortunately there are many ways of detecting these memory structures, that don't include walking an active list of process or loaded modules (dll's).
Instead of doing that, we can look for the structures in memory, because they're still there! They just have been unlinked from the official "source" that tracks them, but because they can still run and function, they must exist in runtime memory.

We just need to find it.

To do that, we can utilize pool scanning, a technique that scans the kernel memory for short tags, that define objects and then parse their data according to a predefined schema and try to squize as much information as possible out of them.
Drawing our focus back to malware, DKOM can achieved through methods like the following:

- By loading a driver as System and having unlimited access.
    
- By using the ZwDebugControl Windows API as System in an elevated session.
