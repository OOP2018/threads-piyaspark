## Threads and Synchronization

This lab illustrates the problem of synchronization when many threads are operating on a shared object.  The general issue is called "thread safety", and it is a major cause of errors in computer software.

## Assignment

To the problems on the lab sheet and record your answers here.

1. Record average run times.
2. Write your explanation of the results.  Use good English and proper grammar.  Also use good Markdown formatting.

## ThreadCount run times

These are the average runtime using 3 or more runs of the application.
The Counter class is the object being shared by the threads.
The threads use the counter to add and subtract values.

| Counter class           | Limit              | Runtime (sec)   |
|:------------------------|:-------------------|-----------------|
| Unsynchronized counter  |   10,000,000       |    0.020366     |
| Using ReentrantLock     |   10,000,000       |    0.560149     |
| Syncronized method      |   10,000,000       |    0.418640     |
| AtomicCounter for total |   10,000,000       |    0.201289     |

## 1. Using unsynchronized counter object

answer the questions (1.1 - 1.3)

1.1) The counter isn't the same(should be zero). It sometimes can be a negative value.

1.2) 0.019707, 0.020366, 0.025667, 0.017614, 0.024348

1.3) It is because threads will work in parallel and sometimes both threads work exactly the same time. It will make the counter not equal 0.

## 2. Implications for Multi-threaded Applications

How might this affect real applications?  

The application won't work accurately. It will make problem for the bank and users.

## 3. Counter with ReentrantLock

answer questions 3.1 - 3.4

3.1) The total is always zero.

3.2) the result will always be zero because threads will not work at the same time.

3.3) It works as a lock. It will work only one thread per time and unlock for another thread. 

3.4) The unlock statement is always called in the finally block to ensure that the lock is released.

## 4. Counter with synchronized method

answer question 4

4.1) It is always zero.

4.2) Because when one thread is executing a synchronized method for an object, other threads that invoke synchronize methods are blocked until the first is done. 

4.3) Synchronized methods enable a simple strategy for preventing thread interference and memory consistency errors

## 5. Counter with AtomicCounter

answer question 5

5.1) Java provides AtomicLong which can be used without any synchronization.

5.2) You would use AtomicLong when you have guarantee that have value can be used in concurrent environment and don't need the wrapper class. Using AtomicLong because long does not allow for thread interoperability.

## 6. Analysis of Results

answer question 6:

6.1) Unsynchronized counter is the fastest and Counter using ReentrantLock is the slowest. 

6.2) I think the best solution can be applied to the broadest range of problem is using AtomicCounter because it will work completely by itself without any synchronized.

## 7. Using Many Threads (optional)

