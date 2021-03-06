# Chapter 1. Introduction

## Exercises
---

**1.12 How do clustered systems differ from multiprocessor systems? What is required for two machines belonging to a cluster to cooperate to provide a highly available service?**

* clustered 시스템은 두 개 이상의 독립적인 시스템을 모아 하나의 시스템으로 사용함으로써 CPU가 여러 개인 것과 같은 형상을 한다는 점에서 multiprocessor 시스템과 다르다. 
* 두 개의 기기로 이루어진 clustered 시스템이 highly available service를 제공하기 위해서는 두 기기가 네트워크를 통해 연결이 되어 있어야한다. 그래야 한 기기가 다른 기기가 fail 된 것을 확인하고, fail 된 기기가 하던 작업을 자신이 가지고 와 지속할 수 있다.

--- 

**1.13 Consider a computing cluster consisting of two nodes running a database. Describe two ways in which the cluster software can manage access to the data on the disk. Discuss the benefits and disadvantages of each.**

* symmetric clustering과 asymmetric clustering 두 가지 형태로 clustered 시스템을 구축할 수 있다. 
* asymmetric clusterting 형태로 구축하는 경우, 하나의 노드는 hot-stand-by 모드를 유지하게 되므로 오직 하나의 노드만 디스크에 접근하게 된다. 따라서 디스크 접근에 대한 별도의 management가 필요하지 않다.

---

**1.14 What is the purpose of interrupts? How does an interrupt differ from a trap? Can traps be generated intentionally by a user program? If so, for what purpose?**

* 인터럽트의 목적은 운영체제와 하드웨어가 상호작용할 수 있는 수단을 제공하는 것이다.
* 인터럽트와 트랩의 주요한 차이점은 발생 주체이다. 인터럽트는 하드웨어 장치에서 발생되지만 트랩은 유저 프로세스에서 발생된다. 또한, 인터럽트는 asynchronous 하지만 트랩은 synchronous하다.
* 트랩은 유저 프로그램에서 고의적으로 생성될 수 있으며, 이와 같은 일을 하는 이유는 커널 모드에서만 사용할 수 있는 기능을 사용하기 위해서다. 

--- 

**1.15 Explain how the Linux kernel variables HZ and jiffies can be used to determine the number of seconds the system has been running since it was booted.**

* Linux 커널의 변수 `jiffies`는 시스템이 부팅되고 난 후 발생한 인터럽트의 횟수를 나타내고, `HZ`는 1초에 발생하는 인터럽트 횟수를 나타낸다.
* 따라서 시스템이 부팅 된 후 몇 초의 시간이 흘렀는지를 알고 싶다면 `jiffies / HZ`를 하면 된다.
* 예를 들어 HZ는 250, `jiffies`는 50이라고 하면 시스템이 부팅된 이후로 `50 / 250 = 0.2`초가 지난 것임을 알 수 있다.

---

**1.16 Direct memory access is used for high-speed I/O devices in order to avoid increasing the CPU’s execution load.**  
**a. How does the CPU interface with the device to coordinate the transfer?**  
**b. How does the CPU know when the memory operations are complete?**  
**c. The CPU is allowed to execute other programs while the DMA controller is transferring data. Does this process interfere with the execution of the user programs? If so, describe what forms of interference are caused.**  

* (a) CPU와 디바이스 간의 데이터 전송은 운영체제의 일부로써 동작하는 디바이스 드라이버를 통해 이루어진다.
* (b) DMA를 사용하는 경우 블록 단위로 데이터 전송이 이루어지는데, 전송이 다 끝난 경우 디바이스 컨트롤러가 인터럽트를 발생시킨다.
* (c) DMA 컨트롤러(디바이스 컨드롤러)가 데이터 전송을 끝낸 경우 인터럽트를 발생시키는데, 이 경우 유저 프로그램의 실행이 중단될 수 있다.

---

**1.17 Some computer systems do not provide a privileged mode of operation in hardware. Is it possible to construct a secure operating system for these computer systems? Give arguments both that it is and that it is not possible.**

* 

---

**1.18 Many SMP systems have different levels of caches; one level is local to each processing core, and another level is shared among all processing cores. Why are caching systems designed this way?**

* SMP 시스템은 여러 개의 CPU가 parallel하게 동작한다. shared cache를 사용하지 않는 경우 각 CPU가 동일한 데이터 A에 액세스 하는 경우 CPU의 local 캐시에 데이터 A에 대한 복사본이 존재하게 된다. 불필요한 데이터 중복이 발생하게 되는 것이다. 하지만 [shared cache를 사용하게 되면 중복된 블록이 존재하지 않는다]().

--- 

**1.19 Rank the following storage systems from slowest to fastest:**  
**a. Hard-disk drives**  
**b. Registers**  
**c. Optical disk**  
**d. Main memory**  
**e. Nonvolatile memory**  
**f. Magnetic tapes**  
**g. Cache**  

* f - c - a - e - d - g - b

---

**1.20 Consider an SMP system similar to the one shown in Figure 1.8. Illustrate with an example how data residing in memory could in fact have a different value in each of the local caches.**

* CPU의 로컬 캐시들로 데이터가 복사되어 CPU가 작업을 처리하며 그 값이 바뀐 데이터가 아직 메모리에 쓰여지지 않은 경우 로컬 캐시의 데이터와 메모리에 있는 데이터의 값이 다를 수 있다.

---

**1.21 Discuss, with examples, how the problem of maintaining coherence of cached data manifests itself in the following processing environments:**
**a. Single-processor systems**
**b. Multiprocessor systems**
**c. Distributed systems**

* (a) single-processor 시스템에서 오직 한 개의 프로세스만 실행되는 경우 cache coherency(캐시 일관성)을 위해 별도로 관리해야할 것이 없다. 다만 여러 프로세스가 실행되는 multitasking 환경에서 여러 프로세스들이 동일한 데이터에 액세스하고자 하는 경우, 항상 각 프로세스가 최신 업데이트된 내용을 참조할 수 있도록 해야한다.
* (b) multiprocessor 시스템에서는 동일한 데이터에 대한 카피본이 여러 캐시에 존재할 수 있다(각 프로세서가 local 캐시를 갖고 있기 때문이다.). CPU들이 parallel하게 동작하기 때문에 cache coherency를 위해 데이터의 값이 변경되면 해당 데이터를 갖고 있는 모든 캐시가 최신 값으로 업데이트 되어야한다.
* (c) distributed 시스템에서는 동일한 파일 자체가 여러 컴퓨터에 있을 수 있기 때문에, 해당 파일들에 대한 데이터 동기화가 필요하다.

---

**1.22 Describe a mechanism for enforcing memory protection in order to prevent a program from modifying the memory associated with other programs.**

---

**1.23 Which network configuration — LAN or WAN — would best suit the fol- lowing environments?**
**a. A campus student union**
**b. Several campus locations across a statewide university system**
**c. A neighborhood**

---

**1.24 Describe some of the challenges of designing operating systems for mobile devices compared with designing operating systems for traditional PCs.**

---

**1.25 What are some advantages of peer-to-peer systems over client – server systems?**

---

**1.26 Describe some distributed applications that would be appropriate for a peer-to-peer system.**

---

**1.27 Identify several advantages and several disadvantages of open-source operating systems. Identify the types of people who would find each aspect to be an advantage or a disadvantage.**