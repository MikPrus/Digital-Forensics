# Executive objects?

Executive objects represent kernel structures like files, mutexes, process, threads etc. in memory. They are Windows C-like structures and are all managed by the system.
For example, the _EPROCESS is the executive object for processes running in the system memory. **EVERY** executive object is managed by the **WINDOWS OBJECT** **MANAGER**, a component of the kernel, implemented in the NT module.

What's interesting from a forensics perspective is that the OS uses, modifies and prepends various medata information to all executive objects. That helps in access control and the number of reference counts to an
object, but also makes correlating objects in memory easier. All executive objects will have the aforementioned headers, excluding objects created by subsystems like the tcpip.sys ( TCP/IP subsystem ).

# Most important Executive Objects:

## _FILE_OBJECT

An object representing an accessed file. It contains the permissions
that were granted during the time the file was accessed, the memory addresses pointing
to portions of the file and finally the file's name. 

## _EPROCESS

A container of a process's private virtual memory space where the threads
of the program are executed. Additionally, the _EPROCESS maintains a list of handles to 
different system resources like files and registry.

## _OBJECT_SYMBOLIC_LINK

Creates aliases that help to map network share paths and removable media to drive letters.

## _TOKEN

Stores SID ( Security Identifiers ) for processes and threads.

## _ETHREAD

Stores the thread object with its CPU context.

## _KMUTANT

Stores the Kernel equivalent of mutexes.

## _DRIVER_OBJECT

Represents a kernel driver in memory.

## _CM_KEY_OBJECT

An instance of an open registry key.

## _OBJECT_TYPE

Metadata describing common kernel object properties.

## tagWINDOWSTATION

Contains the clipboard, atom tables and security boundaries for desktops.

## tagDESKTOP

An object diplaying screen display elements and containing GUI elements like forms, windows etc.
