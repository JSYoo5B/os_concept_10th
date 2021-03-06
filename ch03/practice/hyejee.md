**3.1 Using the program shown in Figure 3.30, explain what the output will be at LINE A.**  
```C
#include <sys/types.h>
#include <stdio.h> 
#include <unistd.h>

int value = 5;

int main()
{
    pid_t pid;
    pid = fork();

    if (pid == 0) { /* child process */ 
        value += 15;

        return 0;
    }
    else if (pid > 0) { /* parent process */
          wait(NULL);
          printf("PARENT: value = %d",value); /* LINE A */

          return 0;
    } 
}
```
* LINE A에서의 아웃풋은 `5`이다.  
* 이 문제에서 확인하고 싶은 개념은 `fork()`를 통해 생성된 child process는 parent process의 address space를 그대로 복사하지만 이것이 두 프로세스가 물리적으로 동일한 메모리 공간을 공유하는 것이 아니라는 것이다. 최적화를 위해 COW(Copy On Write)를 통해 child process가 메모리의 내용을 변경하기 전까지 parent process의 물리 메모리를 참조하고 있을 수 있으나 변경이 일어나면 메모리 복사가 일어나 결국은 서로 다른 물리적 메모리를 차지하게 된다.          

**3.2 Including the initial parent process, how many processes are created by the program shown in Figure 3.31?**  
```C
#include <stdio.h> 
#include <unistd.h>

int main()
{
    /* fork a child process */
    fork();

    /* fork another child process */
    fork();

    /* and fork another */
    fork();

    return 0;
}
```
![ch03-practice-3-2](https://user-images.githubusercontent.com/46441723/175803670-0fba2550-f6ee-403a-bffd-96a2bf584e72.jpg)  
* 8개의 프로세스가 생성된다.  

**3.3 Original versions of Apple’s mobile iOS operating system provided no means of concurrent processing. Discuss three major complications that concurrent processing adds to an operating system.**  

**3.4 Some computer systems provide multiple register sets. Describe what happens when a context switch occurs if the new context is already loaded into one of the register sets. What happens if the new context is in memory rather than in a register set and all the register sets are in use?**  

* 새로운 컨텍스트가 저장될 register set으로 포인터를 변경하고, 해당 register set에 있는 내용을 메모리에 옮긴다. 그리고 새로운 컨텍스트가 메모리에서 register set으로 load 된다.  

**3.5 When a process creates a new process using the fork() operation, which of the following states is shared between the parent process and the child process?**  
**a. Stack**  
**b. Heap**  
**c. Shared memory segments**  

* `c. Shared memory segments`만이 parent process와 새롭게 생성된 child process 사이에서 공유되는 메모리다.  

**3.6 Consider the “exactly once”semantic with respect to the RPC mechanism. Does the algorithm for implementing this semantic execute correctly even if the ACK message sent back to the client is lost due to a net- work problem? Describe the sequence of messages, and discuss whether “exactly once” is still preserved.**  

* ACK 메세지가 유실되더라도 exactly-once semantics는 유지된다. client는 server로부터 ACK 메세지를 받을 때까지 주기적으로 rpc를 보내지만, 서버 측에서 해당 rpc가 정상적으로 처리되었음을 timestamp 등을 통해 판별하여 rpc를 다시 처리하지 않고 ACK를 보낸다.  

**3.7 Assume that a distributed system is susceptible to server failure. What mechanisms would be required to guarantee the “exactly once” semantic for execution of RPCs?**  

