# Windows Emergency Dump Types

The Windows Operating systems has ways of creating memory backups during different activities. There are three types of them that are interesting from a forensic perspective: the crash dump, hiberfil.sys and pagefile.sys.
The first one, crash dump is created when the computer crashes and the second one when it's hibernated. The last, pagefile.sys is the file that supports virtual memory. When the programs running on your computer require memory
than is currently available, they use the pagefile.sys file instead. This is how Paging works and thanks to the pagefile.sys we can retain some memory forensics evidence even if we only have just the disk of the infected machine.

**Note**: ***Windows OS can have up to 16 paging files like pagefile.sys. Be sure to always collect all of them.***

## Ensuring full pagefile.sys collection

To find out the amount of pagefiles used by the system, query these two registry entries:

-> ControlSet001/Control/Session Manager/Memory Management/PagingFiles

-> ControlSet001/Control/Session Manager/Memory Management/ExistingPageFiles
