# What is the Global Offset Table?

Global Offset Table ( GOT ) is a special section of an ELF binary, represented as .got and .got.plt . It that makes the usage of shared libraries possible.
The GOT relocates libraries that point to the same address and updates their static addresses at runtime so that they can run together without any conflicts.
Thanks to got, shared libraries can be used even if they are supposed to be loaded at the same memory address.
