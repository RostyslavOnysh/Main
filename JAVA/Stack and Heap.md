# Stack Vs Heap Java

In Java, memory management is a vital process. It is managed by Java automatically.
The *JVM* divides the memory into two parts: ***stack memory*** and ***heap memory***. From the perspective of Java,
both are important memory areas but both are used for different purposes. 
The major difference between Stack memory and heap memory is that the stack is used to store the order of method execution and local variables
while the heap memory stores the objects and it uses dynamic memory allocation and deallocation. 
In this section, we will discuss the differences between stack and heap in detail.
* ## Stack Memory
The stack memory is a physical space (in RAM) allocated to each thread at run time. 
It is created when a thread creates. Memory management in the stack follows LIFO (Last-In-First-Out) order because it is accessible globally.
It stores the variables, references to objects, and partial results. Memory allocated to stack lives until the function returns.
If there is no space for creating the new objects, it throws the java.lang.StackOverFlowError.
The scope of the elements is limited to their threads. The JVM creates a separate stack for each thread.

* ## Heap Memory
It is created when the JVM starts up and used by the application as long as the application runs. It stores objects and JRE classes.
Whenever we create objects it occupies space in the heap memory while the reference of that object creates in the stack.
It does not follow any order like the stack. It dynamically handles the memory blocks. It means, we need not to handle the memory manually.
For managing the memory automatically, Java provides the garbage collector that deletes the objects which are no longer being used.
Memory allocated to heap lives until any one event, either program terminated or memory free does not occur.
 The elements are globally accessible in the application. It is a common memory space shared with all the threads.
 If the heap space is full, it throws the java.lang.OutOfMemoryError.

## Key Features of Stack Memory
Some other features of stack memory include:
It grows and shrinks as new methods are called and *returned*, *respectively*.
Variables inside the stack exist only as long as the method that created them is running.
It's automatically allocated and deallocated when the method finishes execution.
If this memory is full, Java throws java.lang.StackOverFlowError.
Access to this memory is fast when compared to heap memory.
This memory is threadsafe, as each thread operates in its own stack.
