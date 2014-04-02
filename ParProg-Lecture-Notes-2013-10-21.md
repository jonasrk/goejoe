# ParProg
## 2013-10-21  Terminology and Fundamental Concepts
### #2 Conventional Wisdom Replaced
#### Definition: Parallel computer
A parallel computer is a set of processors that are able to work cooperatively to solve a computational problem

### #3 Terminology & Fundamental Concepts

#### Definition: Concurrency (Nebenläufigkeit)
Capability of a system to have two or more activities in progress at the same time. Demand scheduling and synchronization.

#### Definition: Parallelism
Capability of a system to execute activities simultaneously. Demand parallel hardware.

Write concurrent program. It may be executed in parallel. Can be distributed on different machines.

Processes / threads represent the execution of atomic statements.

#### Definition: Concurrent execution
Interleaving of multiple atomic instruction streams.

Problem: Non-deterministic scheduling. You don't know the order. If instruction streams are independent everything is fine. If the have dependencies (e.g. shared variable) problems occur.

Threads share code, data, files but have own registers and execution stacks.

#### Definition: Race condition
The result of an operation depends on the order of execution.

### #4 Deadlock, Livelock, Race condition

#### Definition: Deadlock
Two or more processes / threads are unable to proceed.

#### Definition: Livelock
Two or more processes / threads continuosly change their states in response to changes in the other processes / threads.

#### Example: Race condition
    void echo() {
        char_in = getchar();
        char_out = char_in;
       putchar(char_out);
    }

#### Definition: Starvation
A runnable process / thread is overlooked indefinitely.

#### Definition: Atomic Operation
Function or action implemented as a sequence of one or more instructions. Appears indivisible to others. Executed as a group or not executed at all

#### Definition: Mutual Exclusion
The requirement that when one process / thread is using a resource, no other shall be allowed to do that.

#### Definition: Ressource
Hardware ressource: devices. Task of operating system is to manage (abstract) them.

Shifting to Parallelism we have multiple execution units.

#### Definition: Speedup
Do it faster. Run the same thing in half the time.

#### Definition: Scaleup
Same application with more throughput. Run the same thing in the same time with double the amount of data. E.g. Webservers, databases, fileservers.

#### Definition: Parallelism by Task, Execution unit, Processing element (Mattson)
* Task: Parallel program breaks a problem into tasks.
* Execution unit: Representation of a concurrently running task. Tasks are mapped to execution units during development time.
* Processing element: Hardware element running one execution unit. (E.g. logical processor, core, machine)

#### Parallel Hardware
Hyperthreading, Multicore, Multiprocessing, Multicomputer

### #5 Multiprocessor
#### Flynn's Taxonomy
* SISD: Classical uniprocessor computer
* SIMD: GPU card, multi instruction streams on multiple data items (eg. pixels)
* MISD: no real application
* MIMD: Multicores

* Multiprocessor: Shared memory
* Multicomputer: No shared memory (Shared nothing system, distributed mem, private mem)

### 6# Share Memory
* Shared memory distinguished in UMA and NUMA
* UMA: Equal load and store acces for all processors to all memory
* NUMA: Processors with local memory (local link) but can also acces memory of others.  Delay on memory access according to the accessed region.

#### Example: Intel Nehalem
4 processors with 4 cores each.
What is the problem with NUMA latencys? If you have a lot of requests. If one application gets slow it drags others also down.

