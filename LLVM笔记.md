# LLVM笔记

[中文地址](https://llvm-tutorial-cn.readthedocs.io/en/latest/index.html)

[官网](http://www.cs.toronto.edu/~pekhimenko/courses/cscd70-w20/content.html)

[github](https://github.com/ArmageddonKnight/CSCD70)

## Lecture1 Introduction

![image-20200813161411513](LLVM笔记/image-20200813161411513.png)

![image-20200813161351564](LLVM笔记/image-20200813161351564.png)

![image-20200813164137934](LLVM笔记/image-20200813164137934.png)

![image-20200813164150296](LLVM笔记/image-20200813164150296.png)

### 判断Basic Block

- 第一个指令
- 跳转的一个目标（goto B2等）
- 任何指令立即附上jump

### 源码优化

Local optimizations 

- within a basic block -- across instructions

Global optimizations

- within a flow graph -- across basic blocks

Interprocedural analysis

- within a program -- across procedures (flow graphs)

#### Local optimizations 

![image-20200813165434277](LLVM笔记/image-20200813165434277.png)

#### (Intraprocedural) Global Optimizations

![image-20200813165608383](LLVM笔记/image-20200813165608383.png)

#### Induction Variable Elimination

![image-20200813170607355](LLVM笔记/image-20200813170607355.png)

#### Loop Invariant Code Motion

![image-20200813170634039](LLVM笔记/image-20200813170634039.png)

#### Graph Abstractions

DAG – directed acyclic graph

![image-20200813171326820](LLVM笔记/image-20200813171326820.png)

![image-20200813171358000](LLVM笔记/image-20200813171358000.png)

## Assignment 1

跟着 [课程Docker指南](https://github.com/ArmageddonKnight/CSCD70/tree/master/0-CSCD70_Docker)来，省事很多，建议

```shell
cd ../Assignment1-Introduction_to_LLVM/FunctionInfo

docker run -it --rm -v "$(pwd):/mnt" --name CSCD70_A1 -w /mnt cscd70:6.0 \make -f Optimize.mk all
```

这样最省事，引号包裹是因为在我这会提示`docker: invalid reference format: repository name must be lowercase.`



## Lecture2 Dataflow

### Value Numbering (VN)

![image-20200813190614744](LLVM笔记/image-20200813190614744.png)

![image-20200813191555541](LLVM笔记/image-20200813191555541.png)

### What is Data Flow Analysis

![image-20200813191729797](LLVM笔记/image-20200813191729797.png)

![image-20200813191811960](LLVM笔记/image-20200813191811960.png)

### Static Program vs. Dynamic Execution

![image-20200813192153402](LLVM笔记/image-20200813192153402.png)

### Data Flow Analysis Schema

![image-20200813192836998](LLVM笔记/image-20200813192836998.png)

### Effects of a Statement

![image-20200813193019347](LLVM笔记/image-20200813193019347.png)

### **Effects of a Basic Block**

![image-20200813193147458](LLVM笔记/image-20200813193147458.png)

![image-20200813200312273](LLVM笔记/image-20200813200312273.png)

### Live Variable Analysis

Definition

- A variable **v** is **live** at point *p* if 

    the value of **v** is used along some path in the flow graph starting at *p*. 

- Otherwise, the variable is **dead**.

### Transfer Function

![image-20200813201432248](LLVM笔记/image-20200813201432248.png)

### Flow Graph 

![image-20200813201559932](LLVM笔记/image-20200813201559932.png)

### Reaching Definitions: Iterative Algorithm

![image-20200813202646807](LLVM笔记/image-20200813202646807.png)

### Reaching Definitions: Worklist Algorithm

![image-20200813202655789](LLVM笔记/image-20200813202655789.png)

![image-20200813202714782](LLVM笔记/image-20200813202714782.png)

### Liveness**: **Iterative Algorithm

![image-20200813202456933](LLVM笔记/image-20200813202456933.png)

![image-20200813202506869](LLVM笔记/image-20200813202506869.png)

### Framework

![image-20200813202839687](LLVM笔记/image-20200813202839687.png)

![image-20200813203453249](LLVM笔记/image-20200813203453249.png)

### Descending Chain

![image-20200813204434720](LLVM笔记/image-20200813204434720.png)

### Data Flow Analysis

![image-20200813212157366](LLVM笔记/image-20200813212157366.png)

### Meet-Over-Paths (MOP)

![image-20200813212617608](LLVM笔记/image-20200813212617608.png)

