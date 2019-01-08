# Reasons for concurrency and parallelism


To complete this exercise you will have to use git. Create one or several commits that adds answers to the following questions and push it to your groups repository to complete the task.

When answering the questions, remember to use all the resources at your disposal. Asking the internet isn't a form of "cheating", it's a way of learning.

 ### What is concurrency? What is parallelism? What's the difference?
 > Both words can be defined as something that happens at the same time. However  concurrency, as opposed to parallelism does not actually have to mean that something is happening exactly at the same time, but rather that these things are happening after each other with at an atomic time difference. 
 
 A easier definition found at quora.com is that concurrency is the proporty of a program where two or more tasks can be in progress simultaneously, while parralism is defined as a run-time property where two or more tasks are beeing executed simultaneously.
 
 
 ### Why have machines become increasingly multicore in the past decade?
 > Machines have become increasingly multicore because paracitic capacitance and heat dissipation is restricting the increase in clock frequency by the processor.
 
 ### What kinds of problems motivates the need for concurrent execution?
 (Or phrased differently: What problems do concurrency help in solving?)
 > concurrency helps when multiple tasks have to run at the same task (multi-threading).
 
 ### Does creating concurrent programs make the programmer's life easier? Harder? Maybe both?
 (Come back to this after you have worked on part 4 of this exercise)
 > Concurrent programs makes the programmers life harder, and bugs more difficult to discover since these bugs often are timing-related. It does however make the code more readable and easier to maintain. 
 
 ### What are the differences between processes, threads, green threads, and coroutines?
 > All these things are tings that are happening concurrently. A process is a type of thread that can be considered the mother-thread of a series of child threads. Essentially threads are used for small tasks while processes are used for the more heavy weigth tasks. The most important distinction is however that processes operate in seperate adress spaces while threads do not.
 
 green threads are threads that are scheduled by a runtime library in the user space rather than the kernel space thus not relying on native OS capabilities. Coroutines are routines that can exit when calling other subroutines and continue from where it left when the subroutine returns. Coroutines are essentially a function, but with no return value.
 
 ### Which one of these do `pthread_create()` (C/POSIX), `threading.Thread()` (Python), `go` (Go) create?
 > They are all threads relying on native OS capacibilities thus we should call them threads.
 
 ### How does pythons Global Interpreter Lock (GIL) influence the way a python Thread behaves?
 > GIL assures that only one native thread can execute at a time. This influene the efficiency in the execution of python Threads since the threads are not actually running in parallel, they only switch execution whenever one thread is in a wait state.
 
 ### With this in mind: What is the workaround for the GIL (Hint: it's another module)?
 > Use processes instead. Each process is running a seperate python interpreter with its own address space.
 
 ### What does `func GOMAXPROCS(n int) int` change? 
 > The GOMAXPROCS variable limits the number of operating system threads that can execute user-level Go code simultaneously
