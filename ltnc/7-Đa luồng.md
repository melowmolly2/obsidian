## Concurrency
- Run several programs or several parts of a program in parralel
- A task can be performed asynchronously or in parallel
	- -> Improves the throughput and the interactivity of the program. 
	![](../Assets/Pasted%20image%2020260528225531.png)
## Unit of Concurrency
- Multi-processing - Multiple Processors/CPUs executing concurrently (Unit:CPU)
- Multi-tasking - Multiple tasks/processes running concurrently on a single CPU.
	- OS executes these tasks by switching between them very frequently (Unit:Process)
- Multi-threading - Multiple parts of the same program running concurrently.
	- Dividing the same program into multiple parts/threads and run those threads concurrently (Unit:Thread)
## Process and Threads
- A process is a program in execution running independently and isolated from others
- A thread is a path of execution within a process
	- It has its own call stack but can access shared data of other threads in the same process
- A Java application runs by default in one process
- Within a Java application might have several threads to achieve parallel processing or asynchronous behavior
- ![](../Assets/Pasted%20image%2020260528225908.png)
## Improvements with concurrency
- Concurrency promises to perform certain tasks faster
	- A task = Several subtasks,
	- These subtasks can be executed in parallel
	- -> Save time (Better CPU Utilization)
- The theoretical possible performance gain can be calculated by *Amdahl's Law*.
## Amdahl's Law Illustrated
- If $B$ is the percentage of the program which can not run in parallel and $N$ is the number of processes, then the maximum performance gain is $\frac1{B+\frac{1-B}N}$.
- ![](../Assets/Pasted%20image%2020260528230204.png)
## Saving time
![](../Assets/Pasted%20image%2020260528230303.png)
## Issues with concurrency
- Threads have their call stack but can also access shared data
- Access problem: if several threads access and change the same shared data at the same time
	- Safety failure (inconsistent data)
	- Thread Interference Errors (Race conditions)
- Visibility problem: if thread A reads shared data, which is later changed by thread B and thread A is unaware of this change
	- Liveness failure (e.g., deadlocks)
	- Memory Consistency Errors
# Java Thread
## Creating and Starting a Thread
- By extending Thread class
- By providing a Runnable object
	- Runnable Anonymous Class
	- Runnable Lambda Expression
![](../Assets/Pasted%20image%2020260528230553.png)
```Java
public class ThreadExample extends Thread {
	@Override
	public void run(){
		System.out.println("Inside : " + Thread.currentThread().getName());
	}
	
	public static void main(String[] args) {
		System.out.println("Inside : "+ Thread.currentThread().getName());
		Thread thread = new ThreadExample(); 
		thread.start(); 
	}
}
```
```Java
public class RunnableExample implements Runnable{
	@Override
	public void run(){
		System.out.println("Inside : "+Thread.currentThread().getName()); 
	}
	
	public static void main(String[] args){
		System.out.println("Inside : " + Thread.currentThread().getName());
		Runnable runnable = new RunnableExample();
		Thread thread = new Thread(runnable);
		thread.start();
	}
}
```
```Java
public class RunnableExampleAnonymousClass {
	public static void main(String[] args) {
		System.out.println("Inside : "+Thread.currentThread().getName());
	Runnable runnable = new Runnable() {
		@Override
		public void run() {
			System.out.println("Inside : "+ Thread.currentThread().getName()); 
		}
	};
	Thread thread = new Thread(runnable)
	thread.start(); 
	}
}
```
```Java
public class RunnableExampleLambdaExpression {
	public static void main(String[] args) {
	System.out.println ("Inside : " + Thread.currentThread().getName()); 
	Runnable runnable = () -> {
		System.out.println("Inside : " + Thread.currentThread().getName()); 
	};
	Thread thread = new Thread(runnable);
	thread.start(); 
	}
}
```
# Runnable or thread, which to use?
## The life cycle of a thread 

![](../Assets/Pasted%20image%2020260528231627.png)
# Pausing execution
```Java
public static void main(String[] args) {
    System.out.println("Inside : " + Thread.currentThread().getName());
    String[] messages = {"If I can stop one heart from breaking,",
        "I shall not live in vain.",
        "If I can ease one life the aching,",
        "Or cool one pain,",
        "Or help one fainting robin",
        "Unto his nest again,",
        "I shall not live in vain"};
    Runnable runnable = () -> {
        System.out.println("Inside : " + Thread.currentThread().getName());
        for(String message: messages) {
            System.out.println(message);
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
        }
    };
    Thread thread = new Thread(runnable);
    thread.start();
}
```
## Waiting for completion of another thread
```Java
Thread thread1 = new Thread(() -> {
    System.out.println("Entered Thread 1");
    try {
        Thread.sleep(2000);
    } catch (InterruptedException e) {}
    System.out.println("Exiting Thread 1");
});

Thread thread2 = new Thread(() -> {
    System.out.println("Entered Thread 2");
    try {
        Thread.sleep(4000);
    } catch (InterruptedException e) {}
    System.out.println("Exiting Thread 2");
});

System.out.println("Starting Thread 1");
thread1.start();

System.out.println("Waiting for Thread 1 to complete");
try {
    thread1.join(1000);
} catch (InterruptedException e) {}

System.out.println("Waited enough! Starting Thread 2 now");
thread2.start();
```
# Executor Framework
- Based on producer-consumer architecture
- Executor service decouples submission from execution policy to let developers easily specify and modify the implementation without much of a code change. 
- Tasks are submitted to a thread pool 
- If there are more tasks than the number of active threads → Insert into the queue for waiting
- If the queue is full $\rightarrow$ rejected. 
### Functionalities 
- **Thread Creation**: Methods for creating threads, a pool of threads, the application can use to run tasks concurrently. 
- **Thread Management: Managing the life cycle of the threads in the thread pool. 
	- You don't need to worry about whether the threads in the thread pool are active or busy or dead before submitting a task for execution
- **Task submission and execution**: Methods for submitting tasks for execution in the thread pool and deciding when the tasks will be executed
## Java executor interfaces
- `Executor` - A simple interface that contains a method called `execute()` to launch a task specified by a `Runnable` object
- `ExecutorService` - A sub-interface of `Executor` that adds functionality to manage the lifecycle of the tasks. It also provides a `submit()` method whose overloaded versions can accept a `Runnable` and a `Callable` (discussed later). 
- `ScheduledExecutorService` - A sub-interface of `ExecutorService`. It adds functionality to schedule the execution of the tasks. 
## ExecutorService example
```Java
public static void (String[] args) {
	System.out.println("Inside : "+Thread.currentThread.getName()); 
	
	ExecutorService executorService = Executors.newSingleThreadExecutor();
	Runnable runnable = () -> {
		System.out.println("Inside : " + Thread.currentThread().getName());
	};
	
	System.out.println("Submit the task specified by the runnable.");
	executorService.submit(runnable);
	executorService.shutdown();
}
```
![](../Assets/Pasted%20image%2020260529074521.png)
## ExecutorService example with multiple threads and task
![](../Assets/Pasted%20image%2020260529081554.png)
## Thread Pool
![](../Assets/Pasted%20image%2020260529081624.png)

## Callable 
- `Runnable` object to define the tasks that are executed inside a thread
- -> What if you want to return a result from your tasks?
- -> Java provides a `Callable` interface
- A `Callable` is similar to `Runnable`, except it can return a result and throw a checked exception
- `Callable` interface has a single method `call()` to contain the code executed by a thread
## Callable examples
```Java
Callable<String> callable = new Callable<String>() {  
	@Override  
	public String call() throws Exception {  
		// Perform some computation  
		Thread.sleep(2000);  
		return "Return some result";  
	}  
};  
//a lambda expression  
Callable<String> callable = () -> {  
	// Perform some computation  
	Thread.sleep(2000);  
	return "Return some result";  
}
```
## Executing Callable tasks
- A `Callable` can be submitted to an executor service for execution
	- What about the `Callable`'s result?
	- How do you access it?
	- When the result of the submitted task will be available
- Future can be used to fetch the result of the task when it is available
## Future & Callable Example
```Java
ExecutorService executorService = Executors.newSingleThreadExecutor();

Callable<String> callable = () -> {
    System.out.println("Entered Callable");
    Thread.sleep(2000);
    return "Hello from Callable";
};

Future<String> future = executorService.submit(callable);

// This line executes immediately
// Do something else while callable is getting executed
// Retrieve the result of the future

// Blocks until the result is available
String result = future.get();
System.out.println(result);

executorService.shutdown();
```
```Java
Future<String> future = executorService.submit(() -> {
    Thread.sleep(2000);
    return "Hello from Callable";
});

while(!future.isDone()) {
    System.out.println("Task is still not done...");
    Thread.sleep(200);
}

System.out.println("Task completed! Retrieving the result");
String result = future.get();
System.out.println(result);

executorService.shutdown();
```
## Cancelling a Future 
- Cancelling a future by using `Future.cancel()` method
- The `cancel()` method accepts `mayInterruptIfRunning` 
	- `True`: the thread that is currently executing the task will be interrupted. 
	- `False`: in-progress tasks will be allowed to complete
- `isCancelled():` check if a task is canceled or not
- After the cancellation of the task, `isDone()` will always be true. 
## `invokeAll` & `invokeAny` 
**Submit multiple tasks and wait for them all to complete
- Executing multiple tasks by passing a collection of `Callables` to the `invokeAll()` method
	- `invokeAll()` returns a list of `Futures` 
	- Any call to `future.get()` will be blocked until all the `Futures` are complete. 
***Submit multiple tasks and wait for any one of them to complete*** 
- The `invokeAny()` method accepts a collection of `Callables` and returns the result of the fastest `Callable`. 
# Synchronization
## Issues with concurrency
- Threads have their call stack but can also accdess shared data
- **Access problem**: if several threads access and change the same shared data at the same time
	- Safety failure (inconsistent data)
	- Thread interference Errors (Race conditions)
- **Visibility problem:** if thread A reads shared data, which is later changed by thread B and thread A is unaware of this change 
	- Liveness failure (e.g., deadlocks)
	- Memory Consistency Errors
![](../Assets/Pasted%20image%2020260529155550.png)
![](../Assets/Pasted%20image%2020260529155701.png)
## Synchronization
**How do we avoid those problems?** 
1. Only one thread can read and write a shared variable at a time
	- When one thread is accessing a shared variable, other threads should wait until the first thread is done
	- This guarantees that the access to a shared variable is `Atomic`, and that multiple threads do not interfere
2. Whenever any thread modifies a shared variable, it automatically establishes a happens-before relationship with subsequent reads and writes of the shared variable by other threads
	 - This gurantees that changes done by one thread are visible to others. 
**Synchronized Methods**
- The `synchronized` keyword makes sure that only one thread can enter the sync methods at one time
**Synchronized Blocks**
- Java internally uses a so-called *intrinsic lock* or *monitor lock* to manage thread synchronization. Every object has an intrinsiclock associated to it. 

```Java
ExecutorService executorService = Executors.newFixedThreadPool(10);

Counter counter = new Counter();

for (int i = 0; i < 1000; i++) {
    executorService.submit(() -> counter.increment());
}

executorService.shutdown();
executorService.awaitTermination(60, TimeUnit.SECONDS);

System.out.println("Final count is : " + counter.getCount());
```
```Java
class Counter {
    int count = 0;

    public synchronized void increment() {
        count = count + 1;
    }

    public int getCount() {
        return count;
    }
}
```
## Volatile Keyword
- `Volatile` keyword is used to avoid memory consistency errors in multithreaded programs
	- It tells the compiler to avoid doiong any optimizations to the variable
	- If you makr a variable as `volatile`, the compiler won't optimize or reorder instructions around that variable. 
## Locks
- `ReentrantLock` is a mutually exclusive lock with the same behavior as the intrinsic/implicit lock accessed via the synchronized keyword
	- Thread that currently owns the lock can acquire it more than once without any problem. 
- The `ReentrantLock` also provides various methods for more fine-grained control
- the `tryLock()` method tries to acquire the lock without pausing the thread.
	- If the thread couldn't acquire the lock because it was held by some other thread, then it returns immediately instead of waiting for the lock to be released. 
```Java
class ReentrantLockCounter {
    private final ReentrantLock lock = new ReentrantLock();

    private int count = 0;

    // Thread Safe Increment
    public void increment() {
        lock.lock();
        try {
            count = count + 1;
        } finally {
            lock.unlock();
        }
    }
}
```
## `ReadWriteLock` 
- `ReadWriteLock` consists of a pair of locks - one for read access and one for write access. 
	- The read lock may be held by multiple threads simultaneously as long as the write lock is not head by any thread
- `ReadWriteLock` allows for an increased 