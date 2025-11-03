## What is stack? What is heap?
Once you got an executable program (maybe after spending hours of programming, bringing your idea into life in the form of a computer program) you shall somehow run it to make it satisfy your needs. Thus this program will be a process, because it is consuming resources from your machine.
One of the resources is the memory, or the RAM (Random access memory). So there is a memory region associated for each process, this is also called address space or the memory space of that process. And here where the processes code and data are stored. This memory space include the code, global initialized & uninitialized variables, stack, heap, the read only data `rodata`, and there might be more sections as well.

![[process-address-space.excalidraw]]

Now the address space for each process, MUST not be accessed by other processes, it must be protected, if a process try to access a memory space that it does not own, a segmentation fault will rise and the process will, more likely, be terminated by the OS.

Now here in this talk we shall explore the stack and the heap.

## What is stack?
As we had mentioned before, it is a memory section that of a process memory space. This section will store local variables. The variables that you initialize in your functions, these variables are handled automatically by the compiler and you need not to worry about freeing them. 
The stack is highly used when you perform a function call from some location in your program. The stack after the function call will store things like:
- Return address.
- The old stack frame (base pointer -> `EBP`).
- The function parameters.
- The local variables of the function that is being called.
- Some registers.

This is example of a calling convention such as the cdecl (C declaration), this convention describes exactly what is happening under the hood when a function called. And this might be the topic of another talk. Basically I am just trynna show you how the role of the stack effective is. 

## What is heap?
The heap, is another important section in the process address space. It stores the the data that you need to manually handle them, I mean you can now allocate memory as much as you want (not if you are out of memory) and free this memory whenever you want to. This is very useful when you want to use array or string that you don't know the size of yet and want to construct the size during the runtime. But it is slower than the stack but bigger than it. Here you can use functions like `malloc()`, `realloc()`, `aligned_alloc()`, `free()`, these functions are part of the C standard library `<stdlib.h>`.
