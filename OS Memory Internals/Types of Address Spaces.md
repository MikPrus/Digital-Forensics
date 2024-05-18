
# What is an Adress Space?

An Address Space is an interface that allows for interacting with the contents of the RAM memory in an easygoing and reliable way. 
If needed, it also handles address translation of virtual addresses to physical addresses. What's more it takes off the burden of understanding specific properties of memory dumps ( like crash/hibernation dump headers ) of the user conducting forensics investigations. An AS handles all of these specifics, providing a transparent access to underlying memory contents.

## Types of AS's

There are two main Address Spaces that are needless to know and understand. Virtual and Physical.

## Virtual Address Space

The Virtual Address Space represents the memory as the processes running on the computer see it. It contains all RAM memory that is not 
paged or moved to secondary storage. To be concise, although this Address Space is a one entity, it can be divided into two parts: user mode and kernel mode, with each part representing
a different set of processes, one in normal memory and the other one in the kernel memory.

## Physical Address Space

The Physical Address Space represents the whole RAM, with the both the data that is paged and the data that is memory resident. It is the AS that always gets used after virtual-to-physical address translation, when 
we want to use/extract/find something in computer memory. 
