# Recovering Memory Evidence from Disk

With high probability you will face situations where a memory dump is not available and all that you've
got is the disk of the machine you need to investigate. Fortunately, in such a situation not all hope is
lost regarding memory forensics. 
For instance, Windows has two files that contain memory data and are saved to disk: hiberfil.sys and pagefile.sys
Hibernation.sys is created when a computer is hibernated, so it may not always be available, but the other one, pagefile.sys
probably will be. It is the file responsable for Paging on Windows and it contains the data that the programs couldn't fill into
the main physical RAM memory.

## Retrieving Hiberfil.sys

Use the fls tool to find the node number for hiberfil.sys, then
use icat to carve it out:

fls -o 2048 disk_image.dd | "hiberfil.sys"

icat -o 2048 disk_image.dd file_node_number > hiberfil.sys


## Retrieving Pagefile.sys

Query the following two registry entries to find the location of the pagefiles ( there can be up to 16 of them )

-> ControlSet001/Control/Session Manager/Memory Management/PagingFiles

-> ControlSet001/Control/Session Manager/Memory Management/ExistingPageFiles
