---
title: "进程与线程"
date: 2020-06-05T16:20:00+08:00
draft: false
---
进程与线程是计算机中十分重要的两个概念，但不易理解。要想理解进程与线程的关系，首先要明白什么是计算机程序。


什么是计算机程序？这个问题很不好回答，我们来从计算机的发展看一看。

最初的计算机，从打孔纸带上识别不同的命令以完成不同的计算。研究人员把自己需要的运算任务分解成不同的命令，再把这些命令按顺序打在打孔纸带上，交给计算机进行计算。计算机不需要知道自己在计算什么，它只要识别打孔纸带上的命令序列，一个一个命令地执行就行了。这个根据任务分解而成的命令序列就是程序。

所以说，一个计算机程序就是需要计算机完成的一个任务，编程就是把计算机能识别的命令进行不同的排列组合以完成某种特定的任务，编出来的这个命令列表就叫程序。通俗地说，程序就是任务，任务就是程序。计算机执行任务的时候，就读取这个程序并执行其中的命令，这就叫做一个进程，也就是正在进行的程序的意思。

早期的计算机里面只有一个CPU，同一时刻只能执行一个任务，其它任务要执行只能等它执行完。而计算机十分昂贵，人们希望它能够同时（至少看起来像是同时）做多件事以充分利用运算资源。如果有两个程序需要执行，程序员就需要仔细安排两个程序的执行计划：这个任务执行一会儿就停下，让计算机执行另一个任务，再过一会儿再切换回来。只要切换得足够快（比如Linux是每5毫秒切换一次），那么看起来就像是多个任务同时在进行，这样就可以在只有一个CPU的计算机上执行多任务了。

后来人们就把这个安排任务执行计划的部分单独提取出来做成一个程序，并给它取名为调度器。调度器负责计算机的任务调度，哪个进程可以执行，哪个要排队，都要服从它的安排，包括它自己的执行也是如此。调度器后来成为多任务操作系统的核心部分，它还有个更高级的名字叫做“进程管理”。
