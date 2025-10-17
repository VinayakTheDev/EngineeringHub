![[Java.png]]

- Process by which JVM automatically handles allocation and deallocation of memory.
- JVM uses [[Garbage Collection (GC)]] to remove unused objects.

### Java Memory Structure
- Defines runtime data areas that are created by JVM and threads in program.
- JVM created areas are destroyed once JVM exits, thread created areas are destroyed once the method execution is finished.

### HEAP AREA
--- 
- **Shared** runtime Created by JVM when JVM starts. 
	- **Objects** 
	- **Arrays**
	are stored in Heap.
- JVM allows to adjust heap size.
- When `new` keyword is used, object is created in **heap** and reference is stored in **stack**.
- GC in Heap is mandatory.
---

### METHOD AREA
--- 
- This is **logical part** of Heap, which means this is also stored in Heap area only. But some JVM stores it outside the heap.
- used to store class-level info viz.,
	- **Class Structure**
	- **Method bytecode**
	- **Static variables**
	- **constant pool**
	- **Interfaces**
- The size can be fixed or dynamic.
- GC is not guaranteed, it depends on JVM implementation.
---
### JVM STACK AREA
---
- Stack is created when a thread is created.
- Used to store method execution data including 
	- **local variables,** 
	- **method arguments** 
	- **return addresses.**
- Each thread has own stack ensuring thread safety.
- Size can be fixed or dynamic.
- Memory of stack need not be contiguous.
- Once method completion executions, its associated stack is removed automatically.
---
### NATIVE METHOD AREA
---
- Known as C-stack
- Memory allocated for each thread when it is created 
- can have either a fixed or dynamic size.
- Handles execution of native methods that interact with Java code
---
### PROGRAM COUNTER (PC) REGISTERS
---
- Each JVM thread has a PC register
- For non-native methods, it stores the address of current instruction.
- For native methods, PC value si undefined.
- On some platforms, the PC can also store a return address or native pointer.
---




| Heap                                                       | Stack                                                       |
| ---------------------------------------------------------- | ----------------------------------------------------------- |
| Created by JVM when JVM starts                             | Created by threads when thread is created                   |
| Stores objects and instance variables                      | Stores local variables and method calls.                    |
| Larger but slower                                          | Smaller but faster                                          |
| Random Access                                              | LIFO                                                        |
| Allocation is manual (`new`) but deallocation is automatic | Allocation and deallocationis automatic, depends on Thread. |
| Long-lived (till JVM does not exits)                       | Short-lived (till thread exists or method duration)         |
| Shared among all threads, needs sync                       | Each thread has it's own stack. (thread-safe)               |


> Static Variable is stored in Method area
> Instance Variable is stored in Heap area
> Local Variable is stored in Stack area




Further Reading:
https://www.geeksforgeeks.org/tag/java-jvm
