2025.5.18

继续着手课程[CMU 15-213 Introduction to Computer Systems](https://www.cs.cmu.edu/afs/cs/academic/class/15213-f15/www/index.html)的作业[Bomb Lab](https://csapp.cs.cmu.edu/3e/bomblab.pdf)

- 阅读汇编代码，通过reverse engineer来手动还原出 `string_length` 与 `strings_not_equal` 两个函数逻辑。
- 开始熟悉汇编中 `jne`, `je`, `jmp`等jump类指令
- 对于CPU register中存储的究竟是什么有了进一步了解，熟悉了`%eax` 和 `%rax` 在CPU指令中的区别（为了检验自己确实明白，尝试从source code来推理手动写出assembly code, 从而与disassembled code进行对照）
- 开始初步研究strings如何隐藏在程序中，以及如何从binary文件中找到其所在的memory address和对应的bytes