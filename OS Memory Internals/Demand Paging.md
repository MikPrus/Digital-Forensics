# Demand paging 

Memory is limited. How can we manage it in the most effective way and squeze the most out of it?
For example, when we want to execute a process a memory, it needs to be fully loaded into memory, right? How could we optimalize
the memory used and introduce more flexibility and effectivity? Imagine the example above, we want to load and run a process in memory. Let's suppose it's quite big, contains a lot of data and dependencies.

Going further, let's imagine that the most important part of the program, the elements that allow for its normal functioning are actually a pretty small
part in comparison to the whole program. Having that in mind, instead of loading the whole program at once, we could just load the most important parts, and then load additional ones if they're explicitly
needed. This method is called Demand Paging. 

Using it, we can save some space and if necessary, we can load further elements of the program into memory through page faults.

# How Demand Paging decides which memory regions are resident?

As explained above, demand paging determines which regions of the memory are resident ( in physical memory ) and which are not. 
This policy is based on the locality of reference. This observation states that when processes are loaded, the addresses in their neighbourhood are very likely to be needed as well.
That way things that are in close proximity to each other can be loaded fast, without big delays or interruptions. Respectively, the things that according to this rule are deemed not worthy 
of beeing loaded into main memory are moved to secondary storage to save precious space.

The most common secondary storage types include:

- partitions
    
- internal disks
    
- files
