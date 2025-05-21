2025.5.20

学习

- 了解stack frame中包含的数据（return address, saved `%rbp`, local variables, spilled registers, extra function arguments），以及它如何随着`%rsp`  stack pointer移动而变化，以及它们如何受到 `push`, `pop`, `call`, `ret` 等instructions的影响
- 巩固基础，了解到`mov 0x14(%rsi), %rax` 和 `lea 0x14(%rsi), %rax` 的区别，以及Load 4 bytes from the memory address into register的含义
- 完成了课程作业Bomb Lab第二道题目

阅读：

- 《早安，怪物》：Peter是在加拿大出生的华人，他的母亲在他小时候曾将他锁在封闭的阁楼上多年，导致他长期以来不懂得感知和表达情绪、畏惧亲密接触（渴望能够靠近异性，但却有心理因素导致的阳痿）、习惯了母亲的打压和批评（与此同时却又总是在维护母亲“她做这一切都是为了这个家好”），在和心理治疗师的共同努力下，逐步成长为情感丰富而有旺盛生命力的人，与此同时也发现，他的母亲之所以这样不近人情、没有母性、只看重金钱，是因为小时候在越南期间遭受了她母亲的虐待，每天被烟卷烫伤来取悦来访的法国殖民者客人。

开心感激：

- 《早安，怪物》的内容非常精彩给人启发，沉浸式阅读了两个小时
- 晚上重新捡起曾经的爱好，用手机录视频自言自语来回顾近期生活，思考学习和找工作



2025.5.19

学习

- 明白了memory的最小单位是one byte, 学会了从memory address中读取出continuous multiple bytes来得到数据，通过从 `objdump -s -j .rodata bomb | less ` 之中提取出字符串 `"Border relations with Canada have never been better."` 而成功通过了Bomb Lab第一道题目！
- 了解到并不是所有函数都会出现在disassembled code中，例如 `__isoc99__sscanf` 这种标准库函数其实藏在 `/lib/x86_64-linux-gnu/libc.so` 中
- 开始熟悉instruction `cmp` 和 `jg` 的组合使用，进一步熟悉 `ZF`, `SF`, `CF`, `OF` 等condition flags

阅读

- 《早安，怪物》：Laura八岁时发现母亲死在床上，九岁时被父亲遗弃，无奈之下为弟弟妹妹扮演了妈妈的角色，在长期的成长过程中形成了牢固的自我防卫机制，认为烂人是理所应当，表达爱意和善意是匪夷所思难以接受的行为。在心理治疗师的帮助下，她逐渐建立起自己的边界，了解到心理发育健全的人所具有的行为模式，最终成为了一个懂得表达和接受情感的更为完整的人。
- 《当我谈跑步时》：村上春树不喜欢竞技或合作型体育项目，跑步却完美契合他的偏好。他跑步的训练量是每周跑六天，每天跑十公里。他坚持每年都去跑马拉松全程，成绩长期维持在3小时30分左右，但是随着身体机能下降，成绩逐渐跌落至4小时的水准。

开心感激：

- 和小莞聊天交流近况很开心，另外小莞建议我可以采纳Tiny Habits中的积极心理学方式，给自己的日常增添自我鼓励和赞美，从而提高整体能量



2025.5.18

学习：继续着手课程[CMU 15-213 Introduction to Computer Systems](https://www.cs.cmu.edu/afs/cs/academic/class/15213-f15/www/index.html)的作业[Bomb Lab](https://csapp.cs.cmu.edu/3e/bomblab.pdf)

- 阅读汇编代码，通过reverse engineer来手动还原出 `string_length` 与 `strings_not_equal` 两个函数逻辑
- 开始熟悉汇编中 `jne`, `je`, `jmp`等jump类指令
- 对于CPU register中存储的究竟是什么有了进一步了解，熟悉了`%eax` 和 `%rax` 在CPU指令中的区别（为了检验自己确实明白，尝试从给定的source code出发手动写出assembly code, 与disassembled code进行对照）
- 开始初步研究strings如何隐藏在程序中，以及如何从binary文件中找到其所在的memory address和对应的bytes

阅读：

- 《普罗旺斯的一年》：“土耳其式马桶”的反人类设计；去车站咖啡店品尝已经经营数十年的老板的手艺；和朋友们玩法式滚球到日落

开心感激：

- 和GPT讨论当前生活浑浑噩噩、强度低、没能处于兴奋和专注之中，有了初步的想法和对策，开始执行每日汇报
- 和小唐聊天讨论她家中的变故，给予她聆听和支持，鼓励她怀着强者心态去勇敢沟通，把令人恼怒和痛苦的家庭问题转化为锻炼综合能力的机会。很高兴我能够帮助到我的老朋友。