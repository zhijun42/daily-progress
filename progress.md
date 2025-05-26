2025.5.2.5

学习 Computer Networking

- Learned more about HTTP and DNS; Learned about SMTP

阅读：

- 《早安，怪物》：投入两个小时阅读了最后一个故事。Madeleine的经历很有趣，让我第一次意识到「不配得感」竟然可以强烈到这种程度，以至于支配一个人的生活，哪怕她十分优秀出众，也依旧发自内心地认为自己是个丑陋邪恶的怪物——来自她母亲的长期洗脑。作者作为经验丰富的心理学家，却也会犯下新手级别的错误：过早透露自己知道的信息，剥夺了让对方独立自主领悟的机会。同时，作者发现，原来自己对于Madeleine和她父亲产生反移情，源于作者自己在青少年时期曾经经历的创伤，而这份伤害甚至连她本人都没有意识到。

开心感激：

- 《早安，怪物》这本书读完了 I enjoyed every minute reading it!
- 在Bilibili上看到视频讨论了一个法律案件：男女双方自主发生了两次性行为，并在事后保持聊天，女方在父母的要求选择报警，最终法院认定男方犯强奸罪而入狱三年。这个案件值得思考，女方「事前同意但事后反悔」的行为让人思考强奸罪行的定义和边界是什么，弱势群体在舆论上拥有的优势，中国社会年轻人的婚恋观以及长期的出生率会如何受到影响



2025.5.24

学习：

- TiDB
  - Learned about decorrelated subquery; Discussed about a SQL example to see how TiDB decides whether a query can be successfully decorrelated, and how that affects the JOIN type (`HashJoin` or `CorrelatedNestedLoopJoin`) and the number of RPCs between TiDB and TiKV. 
- Computer Networking: Started reading the book [Computer Networking: a Top Down Approach](https://gaia.cs.umass.edu/kurose_ross/index.php)
  -  Learned about the nodal delay types happening at a node in the network: nodal processing delay, queuing delay (this reminds a bit of the queueing theory that I briefly studied at a graduate statistics course ), transmission delay (the speed that packets get pushed out of the queue, coule be causing packet loss), propogation delay (this is where the speed of signal/information is bounded by the speed of light). 
  - Learned about the difference between circuit switching and packet switching. I love the analogy of restaurants that require reversations versus those prefer walk-ins.
  - Learned about ISPs at different hierarchy and how pricing/cost can affect how a node wants to connect the another node (could be through the top-tier ISP, could be directly peer-to-peer)
  - Briefly learned about network security topics like (DDoS attack, packet sniffing, zero trust, etc). I will keep these topics in mind when reading through the book.

阅读：

- 今天没有阅读，只是在微信读书上随意浏览了一下用户书评

开心感激：

- 这么多年来，我一直都想好好地学习一番Networking相关内容，尤其是在工作中对于AWS VPC Ingress/Egress等话题感到困惑无助时，我意识到自己的计算机基础很差。现在，我终于行动了起来。其实理论上来说，自从我去年辞职后我就有充足的时间来学习，但我却迟迟没有开启这项内容，直到今天我终于感到厌倦，无法忍受拖延了
- 和GPT讨论后明确了用英语沟通和讨论daily report如何能够带来更多启发和思考，舒畅了许多
- 自录了视频讨论了学习与生活，感到自己清醒了一些。傍晚到江边跑步和散步，思考调整自己的情绪
- 老爸老妈用心烹饪的老鸭汤非常好喝



2025.5.23

学习：TiDB源代码

- 整理提交了第一份pull request来删除`logicalOptimize` 中的无效变量 `interactionRule`, 初步熟悉了TiDB Github workflow和粗略看了CI （我认为Github设计远远不如GitLab好用而人性化）
- 设置breakpoint来详细阅读 `PlanBuilder` 中的函数 `buildTableRefs`,  `buildDataSource`, `buildSelect` 等，每个函数都十分巨大（三四百行代码）而却没有清晰明确的unit test, 我对此感到很惊讶，需要深度研究一下test设计

阅读：

- 《早安，怪物》：沉浸投入两个小时阅读了Alana的故事，她所遭受的苦难和展现出的韧性令人震撼。

开心感激：

- 《早安，怪物》太精彩了！非常愉快的阅读体验
- 下午和老爸去打羽毛球，双方都有一些不错发挥不错的回合。最近几个月里，我们每隔几天就会一起打球。
- 晚上睡觉前和爸妈在客厅看多哈乒乓球世锦赛，王楚钦和孙颖莎的混双比赛尤其有趣



2025.5.22

学习：

- 阅读CSAPP教材，深度研究教材中的例子——不只是简单阅读，而是尝试从C代码中写出汇编代码与教材进行对比，重点研究二者差别——学习到了stack frame如何分配空间给local variables, extra function arguments
- 阅读TIDB Planner代码并通过breakpoints运行来研究函数依赖，终于看到了 `LogicalPlan.PruneColumns` 在 `LogicalProjection`中的实际应用，我之前对此困惑了很久，`PruneColumns`这个interface有非常多的implementation, 但我却看不到unused columns究竟是如何被删除的，现在终于定位到了 `p.Schema().Columns = slices.Delete(p.Schema().Columns, i, i+1)` 这个实际操作。另外我发现了 `logicalOptimize` 中的无效变量 `interactionRule`

阅读：

- 《早安，怪物》：我希望尽可能地深度且充分吸收书中内容，而不是把它当做消遣读物，于是开始重新阅读Danny的故事，记录了一些小的感悟

开心感激：

- 小唐向我分享了在羽毛球双打比赛获得全胜，以及采纳了我对于沟通的建议，改善了紧张的家庭关系
- 老妈中午煮了排骨汤，老爸傍晚炒了菜并在出门前热情地叮嘱着我吃晚饭。其实自从我去年九月初从美国回到家以来，爸妈每天总是会不嫌麻烦、不嫌重复地管饱我的肚子，从来没有一天例外，毫不夸张地一天都没有。我多次感到过感激，并口头表达过，不过在文字中的记录较少，另外，我被照顾得如此周到，却常常不能珍惜一天的时间，这让我感到沮丧和愧疚。



2025.5.21

学习：

- 完成了课程作业Bomb Lab第三道题目，第四道题目涉及到recursion, 反复尝试后依旧无法理解
- 学习了C语言中的switch语句以及对应的汇编语言

阅读：

- 《早安，怪物》：从Danny的故事中，见识到加拿大政府对当地土著印第安人的残忍的种族文化灭绝，了解到原住民的种族创伤和身份认可困境，被Danny的正直勇敢和觉醒疗愈而深深打动。

开心感激：

- 《早安，怪物》真的太精彩了！
- 好友Noco主动来分享《早安，怪物》的读书感悟，还一起聊了Give and Take的测试问卷



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