Thread Control Block (TCB):
- Thread Identifier: Unique id (TID) is assigned to every new thread
- Stack pointer: Points to the thread’s stack in the process. The stack contains the local variables under the thread’s scope.
- Program counter: a register that stores the address of the instruction currently being executed by a thread.
- Thread state: can be running, ready, waiting, starting, or done.
- Thread’s register set: registers assigned to thread for computations.
- Parent process Pointer: A pointer to the Process control block (PCB) of the process that the thread lives on.

To create a new thread, we create an object of the Thread class.
It takes the ‘target’ and ‘args’ as the parameters.
The target is the function to be executed by the thread whereas the args is the arguments to be passed to the target function.
```python
t1 = threading.Thread(target, args)
```
```python
# To start a thread, we use the start() method of the Thread class.
t1.start()
# In order to stop the execution of the current program until a thread is complete, we use the join() method.
t2.join()
```
```python
import threading
import os

def task1():
    #  We use threading.main_thread() function to get the main thread object.
    # We use the threading.current_thread() function to get the current thread object.
	print("Task 1 assigned to thread: {}".format(threading.current_thread().name))
    # os.getpid() function to get the ID of the current process.
    print("ID of process running task 1: {}".format(os.getpid()))

def task2():
	print("Task 2 assigned to thread: {}".format(threading.current_thread().name))
	print("ID of process running task 2: {}".format(os.getpid()))

if __name__ == "__main__":

	print("ID of process running main program: {}".format(os.getpid()))

	print("Main thread name: {}".format(threading.current_thread().name))

	t1 = threading.Thread(target=task1, name='t1')
	t2 = threading.Thread(target=task2, name='t2')

	t1.start()
	t2.start()

	t1.join()
	t2.join()

```
