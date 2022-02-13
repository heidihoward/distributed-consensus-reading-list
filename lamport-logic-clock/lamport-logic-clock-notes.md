###主要是讲如何对分布式环境中的event进行排序（可以用于进程之间的同步，这对于分布式系统实现至关重要），其中分布式环境扩展一下，包括：多进程，多线程，多核程序

#### Happened before
其中最重要happened before的概念，用来定义偏序，并用精确精确的逻辑时钟来描述happened before

##### 定义

More precisely, we define a clock Ci for each process Pi 
to be a function which assigns a number Ci(a) to any event a in that process.

happened before 在逻辑时钟的表述如下：
C1. If a and b are events in process Pi, and a comes before b, then Ci(a) < Ci(b).
C2. If a is the sending of a message by process Pi and b is the receipt of that message by process Pi, then Ci(a) < Ci(b).

##### 逻辑时钟如何实现happened before？
单进程实现
Each process Pi increments Ci between any two successive events.

进程交互实现
 (a) If event a is the sending of a message m by process Pi, 
 then the message m contains a timestamp Tm = Ci(a). 
 (b) Upon receiving a message m, process Pj sets Cj greater than or equal to its present value and greater than Tm.

#### Total order
逻辑时钟如何描述total order？
先比逻辑时钟Ci，再比进程号Pi，但是这里强调了，全序不是唯一的，根据不同的logic lock实现是不一样的，只有happened before关系组成的偏序才是唯一的

#### 例子
论文举了一个例子来说明全序的用处，来说明全序在分布式系统的中的重要性：例子比较简单，不写了

#### Physical lock
然后引入Physical lock，适当的同步物理时钟近似用户请求真实发生时间的逻辑，论文中的实现参考价值不大，现在已经有HLC的实现了, CRDB都是这样实现的
