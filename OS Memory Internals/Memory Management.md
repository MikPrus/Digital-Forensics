# How is memory managed?

![image](https://github.com/MikPrus/Digital-Forensics/assets/72823731/5fee1484-61bd-4322-90f0-280bbe8eb668)
Source: "The Art of Digital Forensics"

RAM, memory that is used by the operating system to perform operations and execute programs, is divided into so-called pages. These pages need to be organized, so the operation system creates 
a couple intermediate objects for that purpose. These objects are the following: 
- page directory
- page table

These two structures sort and segregate pages in memory. They allow us to find the specific one we're looking for by using the CR3 algorithm.
It works in the following way, when we want to convert a virtual address into a physical (real) one to find data in memory, the CR3 algorithm is used with the virtual address as input. This algorithm firstly
finds the page directory base address, walks it up and finds the right entry, which points to a page table. Then, this entry is used to calculate the respective element in the page table. Finally, yhis element in
the page table points to the memory page that we want to access, great! This is how virtual memory can translated into physical memory ;)

But what really handles this process?

# What is the MMU? 
Memory Management Unit (MMU) is the computer component that makes this process possible. It handles the translation of virtual memory addresses into physical ones, it also moves data into secondary storage or brings it back into memory via page faults if they're needed.


![image](https://github.com/MikPrus/Digital-Forensics/assets/72823731/0b01ea57-fe2b-49c6-8cdf-935052b33084)
