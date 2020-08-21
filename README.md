# LLVM pass

可以先看看 [这里](https://zhuanlan.zhihu.com/p/122522485)

LLVM的核心是一个库。从CSCD70的Assignment1来看，llvm pass可以调用库来输出源代码loop.c里有的函数名称，直接调用该函数的次数，参数个数，Basic Blocks数量和指令个数(FunctionInfo.cpp里完成)和对代码进行优化使其运行更快(LocalOpt.cpp里完成)，优化指加减乘除优化，如

```
x + 0 = 0 + x => x
2 * x = x * 2 => (x + x) or x << 1
a = b + 1, c = a - 1 => a = b + 1, c = b
```

可以参考youn9师傅的[github](https://github.com/y-f00l/f00l_llvm_learn)，里面有他的一些很好的笔记。