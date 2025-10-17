<img width="1235" height="434" alt="Pasted image 20251009191450" src="https://github.com/user-attachments/assets/717a3675-f54c-4909-b476-f7ec6221a7d4" />


## Program (recipe):
- A program is a set of instructions and associated data that is static and is stored on the disk.

## Process (Kitchen):
- In order to run the program, OS kernel creates an env to execute the program (recipe), it is called process (kitchen).
- A process consists of instruction, user data, system data, shared resources like mem, address space, disk (ingredients).
- A program can have several copies of it running at the same time but process belongs to a single program.

## Threads (Individual Chefs):
- Thread is a smallest unit of execution.
- Some state associated to process that will be shared among threads (like, washing area, knife, spoon, ladles) but some state will be private to the threads like cutting area to cutting team, dough mixing area to dough team.
- Shared state is visible and accessible to all threads, spl care should be taken to avoid deadlock or race condition.

Caveats:
- Multiprocessing system - multiple processes get scheduled on more than one CPU.
- Requires hardware support where one system comes with multiple cores or execution takes place in cluster of machines.
- Process dont share resources among themselves but threads share resources allocated including mem address space.

<img width="865" height="634" alt="Pasted image 20251009194001" src="https://github.com/user-attachments/assets/f2df3f7e-1e77-4a4b-8997-2851c125a519" />

## Concurrency Vs Parallelism

![[res/Pasted image 20251009200430.png]]

==concurrency is a single chef rapidly switching between taking orders, preparing dough, and baking pizzas to serve multiple customers, while parallelism is multiple chefs each working on separate pizzas at the exact same time to fulfill orders faster==.

Concurrency: The Skilled, Multitasking Chef:
Multiple tasks are making progress over time by sharing a single resource (the chef or a single processor). It's about efficiently managing tasks, not doing them all at once.

Parallelism: The Team of Chefs:
Tasks are genuinely being executed at the very same time on different resources (different chefs or multiple CPU cores). This truly speeds up the overall process of getting food ready.


==Concurrency is about _dealing_ with lots of things at once. Parallelism is about _doing_ lots of things at once.==

## Co-operative VS Pre-emptive Multi-tasking

A system can achieve concurrency by employing one of the following multitasking models:

- Preemptive Multitasking
- Cooperative Multitasking

|                    | Cooperative Multitasking                                                    | Preemptive Multitasking                                                                           |
| ------------------ | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Control**        | Tasks voluntarily give up control.                                          | The operating system forces tasks to give up control.                                             |
| **Stability**      | Fragile. A single misbehaving task can freeze the entire system.            | Robust. A misbehaving task can be interrupted without harming others.                             |
| **Responsiveness** | Can be poor. Lower-priority tasks may wait indefinitely.                    | Very good. All tasks get a fair slice of CPU time, ensuring a responsive system.                  |
| **Overhead**       | Low. There is little management overhead.                                   | Higher. There is a cost to saving and loading the state of tasks. Context-switches are necessary. |
| **Modern usage**   | Mostly seen in specialized or embedded systems where predictability is key. | The standard for all modern, general-purpose operating systems (Windows, macOS, Linux).           |
## Synchronous VS Asynchronous

|Feature|Synchronous (Dine-in)|Asynchronous (Delivery)|
|---|---|---|
|**Request Handling**|Processed one at a time, in sequence.|Processed concurrently in the background.|
|**Customer Experience**|Must wait for their order to be fully completed before others can be served.|Can do other things while waiting and receive updates later.|
|**Resource Utilization**|Inefficient, as the "cashier" (main thread) spends a lot of time waiting for slow tasks (like baking) to finish.|Highly efficient, as the main thread can continue taking new requests while other workers handle the slow parts.|
|**Responsiveness**|Slower overall throughput due to blocking.|Faster overall throughput and better scalability to handle many requests at once.|
|**Implementation**|Simpler to set up, but doesn't scale well.|More complex to implement, but provides higher performance and better responsiveness.|

## CPU Bound VS I/O Bound

| CPU Bound                                                            | I/O Bound                                                                                     |
| -------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Programs that are compute extensive while IO sits idle are CPU bound | Programs that wait for input or output to complete while CPU sits idle                        |
| Multiple CPUs is used to reduce the time for completion              | Benefits from handing the CPU to other tasks while waiting for I/O, improving CPU utilization |
## Throughput vs Latency

| Throughput                                                    | Latency                                                                           |
| ------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Rate of doing work or amount of work done per unit time.      | Time required to complete task or produce the result                              |
| In multi-threaded implementation, throughtput goes up         | In multi-threaded implementation, latency goes down                               |
| In concurrency, time take to execute a program or computation | In concurrency, time taken to execute all the steps in program and produce result |
### Critical Sections and Race Conditions

### Critical Sections
- Piece of code that can be possibly executed concurrently by more that one thread and shares resources and data.

### Race Conditions
- Race conditions occur when thread runs through critical sections without thread synchronization.
- Thread race to read and write through shared resources and based on the order the execution finishes, program's output changes.
- In a race condition, a thread might access a shared resource that has be worked upon by some different thread at the same time causing the data to be inconsistent.

### Deadlock
- When two threads are not able to make any progress as resource required first thread is held by second and resource required by second is held by first.

### Liveness
Ability of the program to complete the execution in timely manner is called Liveness. 

### Live-Lock
- A live-lock occurs when two threads continuously react in response to actions of the other thread without making any progress.
- Ex: Two vehicles passing a narrow bridge.

### Starvation
- A application can experience starvation when it cannot get CPU time. Other threads continuously use up shared resources.

### Reentrant Lock
- A primitive lock that allows the thread to acquire the same lock multiple times without causing the deadlock.
- When a thread first acquires the lock, the hold count is set to 1, then it is incremented on re-acquisition by the same thread.
- The lock is fully released when the hold count returns to zero, `unlock()` must correspond to every `lock()`

<img width="771" height="381" alt="Pasted image 20251009200104" src="https://github.com/user-attachments/assets/114b15fd-f8ab-461d-bf67-7177550aae2d" />



### Mutex vs Semaphores

| Feature       | Mutex (Pizza Oven)                                                                                           | Semaphore (Delivery Drivers)                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| **Purpose**   | **Mutual Exclusion:** Ensures exclusive access to a single resource.                                         | **Resource Control:** Manages access to a pool of resources.                                                         |
| **Mechanism** | A **locking** mechanism. The resource is locked and unlocked.                                                | A **signaling** mechanism. Threads wait for or signal resource availability.                                         |
| **Value**     | Can only be locked (1) or unlocked (0).                                                                      | An integer counter (permits), representing the number of available resources.                                        |
| **Ownership** | Enforces strict ownership. Only the thread that locks it can unlock it.                                      | Has no ownership. Any thread can signal (release) the semaphore.                                                     |
| **Analogy**   | A single key to a single pizza oven.                                                                         | A sign at the driver dispatch desk showing how many delivery drivers are available.                                  |
| **Use Case**  | Protecting shared data that only one thread should access at a time, like updating the shop's cash register. | Limiting the number of simultaneous connections to a database or restricting access to the pool of delivery drivers. |

A semaphore can potentially act as a mutex if the permits it can give out is set to 1. The imp difference between the two is:
	1. In case of Mutex, same thread must call acquire and subsequent release on the mutex. This is ownership, A mutex is owned by the thread acquiring it till the point the owning-thread releases it.
	2. In binary semaphore, different threads can call acquire and release on the semaphore. there is no concept of ownership
### Semaphore for Signaling

Another distinction between a semaphore and a mutex is that semaphores can be used for signaling amongst threads, for example in case of the classical **producer/consumer** problem the producer thread can signal the consumer thread by incrementing the semaphore count to indicate to the consumer thread to consume the freshly produced item. A mutex in contrast only guards access to shared data among competing threads by forcing threads to serialize their access to critical sections and shared data-structures.
### Implementations
