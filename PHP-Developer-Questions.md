# PHP QUESTIONS

这里将会有 PHP 基础知识、数据库（MySql、NoSql）、分布式系统 等

> 待更新😢

> 总体来说，服务端研发涉及如下技术



- [基础基础](#1)

    - [PHP基础](#1.1)

    - [数据结构](#1.2)

    - [数据库原理](#1.3)

    - [操作系统(Linux)](#1.4)

- [编程能力](#2)

    - [C语言基础](#2.1)

    - [算法](#2.2)

- [扩展技术](#3) 

	- [MySQL](#3.1)

	- [Redis](#3.2)

	- [分布式系统](#3.3)





<h1 id="1">基础基础</h1>

<h2 id="1.1">PHP基础</h2>








<h2 id="1.2">数据结构</h2>

<h2 id="1.3">数据库原理</h2>

<h2 id="1.4">操作系统(Linux)</h2>






> PHP 语言结构例如：array()，echo，empty()，eval()，exit()，isset()，list()，print 或 unset()。这些都不是函数。


#### 抽象类
> PHP 5 支持抽象类和抽象方法。定义为抽象的类不能被实例化。(abstract 修饰关键词)


> 任何一个类，如果它里面至少有一个方法是被声明为抽象的，那么这个类就必须被声明为抽象的。被定义为抽象的方法只是声明了其调用方式（参数），不能定义其具体的功能实现。


> 继承一个抽象类的时候，子类必须定义父类中的所有抽象方法；另外，这些方法的访问控制必须和父类中一样（或者更为宽松）。例如某个抽象方法被声明为受保护的，那么子类中实现的方法就应该声明为受保护的或者公有的，而不能定义为私有的。此外方法的调用方式必须匹配，即类型和所需参数数量必须一致。例如，子类定义了一个可选参数，而父类抽象方法的声明里没有，则两者的声明并无冲突。 这也适用于 PHP 5.4 起的构造函数。在 PHP 5.4 之前的构造函数声明可以不一样的。



#### 对象接口

> 使用接口（interface），可以指定某个类必须实现哪些方法，但不需要定义这些方法的具体内容。

> 接口中定义的所有方法都必须是公有，这是接口的特性。就像定义一个标准的类一样，但其中定义所有的方法都是空的。


> 可以用接口实现多继承，但是本质上PHP是单继承。

```php
	interface iTemplate{
		
	}

	//类中必须实现接口中定义的所有方法，否则会报一个致命错误
	class Collection implements ArrayAccess, Countable, IteratorAggregate, JsonSerializable
	{
	}
```


#### trait

> 自 PHP 5.4.0 起，PHP 实现了一种代码复用的方法，称为 trait。Trait 是为类似 PHP 的单继承语言而准备的一种代码复用机制。Trait 为了减少单继承语言的限制，使开发人员能够自由地在不同层次结构内独立的类中复用 method。Trait 和 Class 组合的语义定义了一种减少复杂性的方式，避免传统多继承和 Mixin 类相关典型问题。

> 从基类继承的成员会被 trait 插入的成员所覆盖。优先顺序是来自当前类的成员覆盖了 trait 的方法，而 trait 则覆盖了被继承的方法。

#### Final 关键字

> PHP 5 新增了一个 final 关键字。如果父类中的方法被声明为 final，则子类无法覆盖该方法。如果一个类被声明为 final，则不能被继承。




#### Static（静态）关键字

> 声明类属性或方法为静态，就可以不实例化类而直接访问。

> 由于静态方法不需要通过对象即可调用，所以伪变量 $this 在静态方法中不可用。

> 静态属性不可以由对象通过 -> 操作符来访问。

>用静态方式调用一个非静态方法会导致一个 E_STRICT 级别的错误。








详情见： [OAuth 2.0 认证的原理与实践](https://waylau.com/principle-and-practice-of-oauth2/)


### 并发

> 死锁

```
	死锁是指多个进程因竞争系统资源或相互通信而处于永远阻塞状态，若无外力作用，这些进程都无法向前推进。

	死锁的原因主要是：（1） 因为系统资源不足。（2） 进程运行推进的顺序不合适。（3） 资源分配不当等。

	产生死锁的四个必要条件：（1） 互斥条件（2） 请求与保持条件（3） 不剥夺条件。（4） 循环等待条件

	避免死锁的一个著名的算法是 银行家算法

	银行家算法是一种最有代表性的避免死锁的算法。又被称为“资源分配拒绝”法。在避免死锁方法中允许进程动态地申请资源，但系统在进行资源分配之前，应先计算此次分配资源的安全性，若分配不会导致系统进入不安全状态，则分配，否则等待。为实现银行家算法，系统必须设置若干数据结构。

```

> 进程间(IPC)通信技术包括

```
	消息传递
	共享内存
	系统管道
	同步
	远程过程调用(RPC)
	socket
```

> 解决并发操作带来的数据不一致性问题，一般采用的方法是？

```
	封锁
```


> 哪些可以用于Linux进程间通讯?
```
管道及(pipe)有名管道
信号（signal）                
报文队列
共享内存
信号量(semaphore)
套接字（socket）
```




> 共享内存 、信号量、


同步机制应该遵循的基本准则 
· 空闲让进：当无进程处于临界区时，表明临界资源处于空闲状态，允许一个请求进入临界区的进程立即进入临界区，以有效利用临界资源
 · 忙则等待：当已有进程处于临界区时，表明临界资源正在被访问，因而其他试图进入临界区的进程必须等待，以保证对临界资源的互斥访问
 · 有限等待：对要求访问临界资源的进程，应保证在有限时间内能进入自己的临界区，以免陷入“死等”状态
 · 让权等待：当进程不能进入自己的临界区时，应立即释放处理机，以免进程陷入“忙等”状态



当我们在局域网内使用ping www.nowcoder.com时，哪种协议没有被使用?



ICMP
ARP
DNS
TCP

选择d，在网络层那3个都会用到，tcp传输层才会用到



进程是资源分配和拥有的单位,同一个进程内的线程共享进程的资源、
线程作为调度和分配的基本单位，进程作为拥有资源的基本单位
在同一进程中的各个线程，才可以共享该进程所拥有的资源

> 轮询任务调度与抢占式任务调度的区别？

轮询调度优点是其简洁性，它无需记录当前所有连接的状态，所以它是一种无状态调度

抢占式调度实现相对较复杂

轮询调度算法的原理是每一次把来自用户的请求轮流分配给内部中的服务器，从1开始，直到N(内部服务器个数)，然后重新开始循环。
抢占式任务调度允许调度程序根据某种原则去暂停某个正在执行的进程，将已分配给该进程的处理机重新分配给另一进程。抢占方式的优点是，可以防止一个长进程长时间占用处理机，能为大多数进程提供更公平的服务，特别是能满足对响应时间有着较严格要求的实时任务的需求。
因为抢占式调度可能会暂停一些进程，需要记录进程的运行状态，较为复杂。轮询式只需要轮流分配资源，调度简单。


下列关于多线程，多进程，多任务的区别与关系描述正确的有？
  线程是指进程内的一条执行线路，或者说是进程中可执行代码的单独单元，它是操作系统的基本调度单元。
  一个进程至少有一个线程，即主线程，也可以有多个线程协同工作。
  进程从主线程开始执行，进而可以创建一个或多个附加线程来执行该进程内的并发任务，这就是基于线程的多任务。



Linux操作系统包括三种不同类型的进程，每种进程都有自己的特点和属性。 
1.交互进程——由一个shell启动的进程。交互进程既可以在前台运行，也可以在后台运行。 
2.批处理进程——这种进程和终端没有联系，是一个进程序列。 
3.监控进程（也称守护进程）——Linux系统启动时启动的进程，并在后台运行。


777 

组外、所有者、组内

三段权限分别为：用户，组内成员，其余用户。
权限：r：4，w：2，x:1

Umask是设置系统创建文件时的默认权限，是创建文件权限补码，对文件来说最大值是6
Umask设为为244，则创建的文件默认权限是422，文件的第一位是‘-’也就是-r---w--w-



###
linux下查看当前网络连接的命令。

netstat


linux下查看磁盘挂载状态的命令式？mount






Linux命令行下如何查找列出/usr/local这个目录下所有包含字符mrtg的文件?
grep -Rn "mrtg" /usr/local



若一台计算机的内存为128MB，则交换分区的大小通常是 。 256MB

关闭linux系统（不重新启动）可使用命令。halt halt就是调用shutdown -h

关机命令有halt init 0 poweroff   shutdown -h 时间，其中shutdown是最安全的
重启命令有reboot, init 6, shutdow -r 时间




建立动态路由需要用到的文件有（）




Linux用户分为：拥有者、组群(Group)、其他（other）
linux中的文件属性过分四段，如  -rwzrwz---
第一段  -  是指文件类型 表示这是个普通文件
文件类型部分
-为：表示文件
d为：表示文件夹
l为：表示链接文件，可以理解为 windows中的快捷方式（link file）

b为：表示里面可以供存储周边设备
c为：表示里面为一次性读取装置
 
第二段  rwz  是指拥有者具有可读可写可执行的权限  
类似于windows中的所有者权限比如 administrator 对文件具有 修改、读取和执行权限
 
第三段  rwz 是指所属于这个组的成员对于这个文件具有，可读可写可执行的权限      
类似于windows中的组权限比如administrators组，属于这个组的成员对于文件的都有 可读可写可执行权限
 
第四段  --- 是指其他人对于这个文件没有任何权限
类似于windows中的 anyone 一样就是说所有人对着个文件都会有一个怎样的权限.


文件系统元数据的 ？


sed命令


在使用mkdir命令创建新的目录时，在其父目录不存在时先创建父目录的选项是 mkdir -p /test/test/demo






在Linux中，每个打开的文件被赋予一个文件描述符(file descriptor)，包括标准输入（stdin），标准输出（stdout）和标准错误输出（stderr），由0,1,2分别描述。

command &> file 表示将标准输出（stdout）和标准错误输出（stderr）重定向至指定的文件file中。 

语法错误。正确的语法是M >& N，M和N都是文件描述符，M在不指定的情况下默认是文件描述符1。

command > file 2>&1，是由两部分组成。首先command>file表示将标准输出（stdout）重定向到文件file中。接下来的2>&1表示将标准错误输出（stderr）输出到文件描述符1指定的位置，即标准输出（stdout）的位置，由于标准输出已经冲定向到文件file中，所以标准错误输出也会重定向到文件file中。

command 2> file 1> file，也可看成是由两部分组成。首先command 2> file，表示将标准错误输出（stderr）重定向到文件file中；1> file，表示将标准输出（stdout）重定向到文件file中。 最终的file中不会包含标准错误输出（stderr）的信息，因为会被之后的标准输出（stdout）覆盖。


stdout（标准输出），输出方式是行缓冲输出的字符会先存放在缓冲区，等按下回车键时才进行实际的I/O操作。 
stderr（标准错误），是不带缓冲的，这使得出错信息可以直接尽快地显示出来。


管道符 | 





以下哪些命令可以查看当前系统的启动时间（）
w、top、uptime


进程由哪几部分组成？

　　①程序。作用：描述进程要完成的功能。

　　②数据集合。作用：程序在执行时所需要的数据和工作区。

　　③程序控制块PCB。作用：包含进程的描述信息和控制信息。它是进程存在的唯一标志。


1.查询中用到的关键词主要包含六个，并且他们的顺序依次为 
select--from--where--group by--having--order by  
其中select和from是必须的，其他关键词是可选的，这六个关键词的执行顺序 
与sql语句的书写顺序并不是一样的，
而是按照下面的顺序来


执行 
from--where--group by--having--select--order by, 

from:需要从哪个数据表检索数据  
where:过滤表中数据的条件 
group by:如何将上面过滤出的数据分组 
having:对上面已经分组的数据进行过滤的条件  
select:查看结果集中的哪个列，或列的计算结果 
order by :按照什么样的顺序来查看返回的数据 



/etc/hosts 设定用户自已的IP与名字的对应表
/etc/gateways 设定路由器 
/etc/resolv.conf    设置DNS 



　计算机网络通信安全的五个目标是
　　(1) 防止析出报文内容；
　　(2) 防止通信量分析；
　　(3) 检测更改报文流；
　　(4) 检测拒绝报文服务；
　　(5) 检测伪造初始化。


要判断IP地址是否在同一个网络，下列哪一项运算正确？ IP与子网掩码
> https://www.zhihu.com/question/29723388


关于堆排序复杂度分析叙述正确的有：
（1）堆排序的时间复杂度为O(nlogn)；
（2）整个构造堆的时间复杂度为O(n)；
（3）堆排序的空间复杂度为O(1)；
（4）堆排序是一种不稳定的排序算法。


dns区域配置文件默认有
localhost.zone、named.local



在MySql中，concat函数的作用是是将传入的参数连接成为一个字符串，则concat（’aaa’,null,’bbb’）的结果是 null 
任何字符串与null拼接为null


session_start() 函数必须位于< html >标签之前 、必须在发送任何HTML、文本信息前调用session_start() 函数    
setcookie() 函数用于设置 cookie，且必须位于  标签之前、cookie 是服务器留在用户计算机中的小文件 


require和include都可以引入并运行指定的文件
在include执行失败或错误时，只产生警告；而require会产生一个致命错误
当处理的文件丢失时，想停止解析脚本应该使用require 




简单工厂模式中的抽象产品角色必须由接口或抽象了来实现
简单工厂模式中只有一个工厂类
工厂方法模式里具有不同的工厂子类


> [数据库范式那些事](http://www.cnblogs.com/CareySon/archive/2010/02/16/1668803.html)



链表是一种物理存储单元上非连续、非顺序的存储结构，数据元素的逻辑顺序是通过链表中的指针链接次序实现的 




以下关于网络延迟的理解 指从报文开始进入网络到它开始离开网络之间的时间


> 线程共享的内容包括：
1.进程代码段
2.进程中的拥有数据（利用这些共享的数据，线程很容易的实现相互之间的通讯）
3.进程打开的文件描述符
4.信号的处理器
5.进程的当前目录
6.进程用户ID与进程组ID

> 线程独有的内容包括
1.线程ID
2.寄存器组的值
3.线程的堆栈
4.错误返回码
5.线程的信号屏蔽码



> SOLID 原则

- 单一职责原则（SRP）： 表明软件组件（函数、类、模块）必须专注于单一的任务。

- 开/闭原则（OCP）：表明软件设计时必须要时刻考虑到（代码）可能的发展（具有扩展性），但是程序的发展必须最少地修改已有的代码(对已有的修改封闭)。

- 里氏替换原则（LSP）：表明只要继承的是同一个接口，程序里任意一个类都可以被其他的类替换，在替换后不需要其他额外的工作程序就能够像原来一样运行。

- 接口隔离原则（ISP）：将大而全的接口拆分成一些小的更具体的接口。

- 依赖反转原则（DIP）：表明一个方法应该遵从依赖于抽象接口而不是一个实例类。






> 用于服务器共享session？

利用NFS共享Session数据
基于数据库的Session共享
基于Cookie的Session共享
使用类似BIG-IP的负载设备来实现资源共享




DML（data manipulation language）：
它们是SELECT、UPDATE、INSERT、DELETE，就象它的名字一样，这4条命令是用来对数据库里的数据进行操作的语言
DDL（data definition language）：
DDL比DML要多，主要的命令有CREATE、ALTER、DROP等，DDL主要是用在定义或改变表（TABLE）的结构，数据类型，表之间的链接和约束等初始化工作上，他们大多在建立表时使用
DCL（Data Control Language）：
是数据库控制功能。是用来设置或更改数据库用户或角色权限的语句，包括（grant,deny,revoke等）语句。在默认状态下，只有sysadmin,dbcreator,db_owner或db_securityadmin等人员才有权力执行DCL

各分E-R图之间的冲突主要有3类：属性冲突、命名冲突和结构冲突。
属性冲突包括属性域冲突和属性取值单位冲突。
命名冲突包括同名异义和异名同义冲突。


结构冲突包括同一对象在不同应用中具有不同的抽象，同一实体在不同分E-R图中所包含的属性个数和属性排列次序不完全相同

共享锁(S锁)和排它锁(X锁)


释义

共享锁:（读取）操作创建的锁。其他用户可以并发读取数据，但任何事物都不能获取数据上的排它锁，直到已释放所有共享锁。
共享锁(S锁)又称为读锁，若事务T对数据对象A加上S锁，则事务T只能读A；其他事务只能再对A加S锁，而不能加X锁，直到T释放A上的S锁。这就保证了其他事务可以读A，但在T释放A上的S锁之前不能对A做任何修改。
 
排它锁
排它锁：排它锁又称为写锁（(eXclusive lock,简记为X锁)），若事物T对数据对象A加上X锁，则只允许T读取和修改A，其它任何事务都不能再对A加任何类型的锁，直到T释放A上的锁。它防止任何其它事务获取资源上的锁，直到在事务的末尾将资源上的原始锁释放为止。
独占锁和共享锁的区别

1.共享锁（S锁）：如果事务T对数据A加上共享锁后，则其他事务只能对A再加共享锁，不能加排它锁。获准共享锁的事务只能读数据，不能修改数据。
排他锁（X锁）：如果事务T对数据A加上排他锁后，则其他事务不能再对A加任任何类型的封锁。获准排他锁的事务既能读数据，又能修改数据。
2.共享锁下其它用户可以并发读取，查询数据。但不能修改，增加，删除数据。资源共享.


数据库范式详解: 减少数据库中数据冗余的过程


1NF + 消去非主属性对键的部分函数依赖 = 2NF。即2NF中，非主属性完全依赖于主关键字；

第一范式就是无重复的列.
说明：在任何一个关系数据库中，第一范式（1NF）是对关系模式的基本要求，不满足第一范式（1NF）的数据库就不是关系数据库。

2NF + 消去非主属性对键的传递函数依赖 = 3NF。即3NF中，属性不依赖于其它非主属性。传递函数依赖，指的是如果存在"A → B → C"的决定关系，则C传递函数依赖于A；

第三范式（3NF）属性不依赖于其它非主属性 [ 消除传递依赖 ]
3NF + 消去主属性对键的传递函数依赖 = BCNF。

（Boyce-Codd 范式）BCNF是3NF的改进形式，即在3NF的基础上，数据库表中如果不存在任何字段对任一候选关键字段的传递函数依赖则符合BCNF。


关系数据模型的三个组成部分中 数据结构、完整性规则、数据操作

用于数据库恢复的重要文件是：日志文件


SQL语言具有的功能 数据定义、数据操纵、数据控制



MySQL5.6开始主从复制有两种方式：基于日志（binlog）；基于GTID（全局事务标示符）。


