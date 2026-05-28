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
	- Thread Interference e