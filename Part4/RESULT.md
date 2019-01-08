Part 4: Result
--------------------

### What happens?
c: The magic number is: -49145   (changes every run)  
go: The magic number is: 1302884 (changes every run)  
python: The magic number is -89197 (changes every run)  
  
### Why?
Intuetively, since we are incrementing the number 1 million times and decrementing it 1 million times one would expect the magic number to be 0 when both threads have finnished. However, because the incrementing and decrementing operations are not atomic operations, but rather consists of three operations load, increment and store, the thread may be interrupted in the middle of an operation which results in unpredictable behaviour.

#### Example running 3 times (assuming deterministic switching between threads):

thread 1 loads i=0.  
thread 2 loads i=0.  
thread 1 adds 1 to i=0, making i=1  
thread 2 subtracts 1 from i=0, making i=-1  
thread 1 stores i=1  
thread 2 stores i=-1  
  
thread 1 loads i=-1  
thread 2 loads i=-1  
thread 1 adds 1 to i=-1, making i=0.  
thead 2 subtracts 1 from i=-1, making i=-2.  
thread 1 stores i=0.  
thread 2 stores i=-2.  
  
thread 1 loads i=0  
thread 2 loads i=0  
thread 1 adds 1 to i=0, making i=1.  
thead 2 subtracts 1 from i=0, making i=-1.  
thread 1 stores i=1.  
thread 2 stores i=-1.  
  
thus, we end up with -1, rather than 0.  



