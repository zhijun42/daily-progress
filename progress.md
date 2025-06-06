## 2025年6月

2025.6.5

学习：

- Briefly learned about socket programing in C++.
- Read a few chapters of the open source book *Everything curl* written by the creator of cURL, Daniel Stenberg. It's astonishing to see how widely curl is used all around the world, especially in devices like Nitendo Switch, vehicles, printer, audio and video equipment, and so many more! I'm much more interested in curl now.
- I seem to struggle a lot with the fundamentals. Today I finally realized that an HTTP request needs the public IP address of the server (I thought we always need the combination of both public and private IPs) and the Host. A simple command  `curl http://cs144.keithw.org/hello ` would actually automatically add the Host header for us.
  - I've long realized a big flaw in my recognition pattern is that I always prefer going deep into certain material to focus on a narrow topic, but barely have any understanding on the basic stuff. I need to work on this.

创作：

- 整理《早安，怪物》中关于Laura的故事素材，我已经把书中的这个章节阅读过两遍，并且对照着英文原文进行补充。我有很多感受感悟想要表达，却又不知从何说起，于是只能先在草稿本上不受限地写下所有想法，我想不出该如何将它们串联起来。我想到了先流水账式地简单写下Laura的经历，她的各种心理症状，以及可以采取的治疗措施。

  我意识到，我很不擅长讲故事，无法做到依照时间线转述书中内容，我所擅长的是用bullet point的形式来展示自己的思考。整体而言，我的写作十分内耗，每写下一句话都要反复斟酌打磨，我既不想写成网络营销账号那样博人眼球的低智力形式，又不想显得过于深沉严肃（我意识到轻盈是我的追求，让人轻松愉悦地阅读，并从中获得启发）；我既想要展示自己的思考深度和认知高度，又不想显摆自己，不想流露出说教的爹味儿或者对于女性群体的不尊重。

  简单来说，我对自己的要求很高，而我却还不具备相应的写作能力（尽管我从2018年起就在坚持写日记和复盘），我又很多批判的不愿同流合污的风格，但又没能培养出属于自己的、能够心安理得地接受和同处的文字风格。目前的我，要不断打磨斟酌每段话才能不这么嫌弃自己，创作的速度可想而知有多慢——最终花费四个多小时写了两千字。另外，完成作品后起标题也是一件相当费时间的事情，又一次地，我希望构想出不落俗套、不哄骗诱导读者的精简题目，但似乎这往往需要灵光乍现的瞬间——我明白的，缺乏灵气，这是我的文字缺陷。

  无论如何，我会坚持写作，坚持分享。我要将盘踞在脑中的想法表达出来。

开心感激：

- 和GPT讨论每日汇报，再次强调了test the walls的重要性，希望能够借此来调整我的个人体系；此外，我将CSAPP和CS144课程的deadline整合到我个人的日历中，以此来推动自己来完成更多任务，战胜自由散漫的本性。
- 终于完成了写作！《早安，怪物》给我带来了巨大的震撼，我对自己发誓一定要为此进行创作表达，不要让它沦落为又一本「读完之后觉得思绪澎湃，但过几天又归于平静」的作品，不要浪费美好的事物，也不要辜负自己的情绪和思考感悟。
- 在微信读书上读《早安，怪物》时，经常能看到一位用户分享某段翻译的英文原文，指出由于国内审核而在翻译上做出的妥协。我向这位用户发消息表达了感谢，得到回复“谢谢你告诉我~”。我喜欢这种传播善意和表达感恩的细小举动，不管有没有收到反馈，我都希望今后可以坚持做下去。
- 在B站上看了「谁是阿尖」的亚马逊雨林旅行视频，被她的旺盛生命力感染。见到了Leticia这个哥伦比亚、巴西和秘鲁三国交界的小镇，见到了阿尖和当地原住民的友好相处。我确认了这是我渴望的旅行风格——学习当地语言（西班牙语）和当地居民产生连接，感谢阿尖提供了这样的优质体验。



2025.6.4

学习

- C++
  - Learned the advantages of modules introduced in C++ 20 and disadvantages (I used to think this is a good feature in C/C++) in header files: repetive parsing to blow up compilation time, order dependencies (be careful of how you do `#include`), inconsistencies (defining the same type/function in two seperate files) and transitivity (a header file needs to consume a lot of other header files). The author tested that compiling a simple helloWorld file using `import std`  is 10 times faster than using `#include <iostream>`, even though the `std` module contains the whole standard library, more than 10 times of information in the `iostream` header.
    - I realized that the adoption of modules has been pretty slow and none of the open source databases have migrated to it.
  - Learned more about the philosophy of Resource Acquisition is Initialization, and how using raw `new` and `delete` can cause disaters like double delete, memory leaks and use after delete. Learned destructors, smart pointer `std::unique_ptr` and Return Value Optimization.
    - Looks like RAII can also be used to manage mutex, which seems promising in avoding deadlocks. I'd like to learn more later.
  - Learned class hierachy, interface inheritance and implementation inheritance, but I still don't feel comfortable enough with classes in C++ and defining methods.

- CS144 lab checkpoint 0
  - Still struggled reading the source code. Learned more C++ basis during reading like file descriptor, iovec, size_t and string_view.
- Networking book
  - Learned that modern TCP implementation uses Selective Repeat protocol. It uses only one timer to keep track of the oldest unacknowledged segment, instead of one timer for each segment. And it has Fast Retransmit (detecting 3 duplicates ACKs). I also briefly learned how TCP uses a ring buffer structure to implement, which reminds me of the ring in the Consistent Hashing algorithm.

阅读：

- 用1个小时来继续梳理《早安，怪物》中Laura的心路历程，我希望能够尽快写出文章来表达我的思考感悟。

开心感激：

- 在下午的一个瞬间感受到这样的学习生活非常充实，感到很幸福。



2025.6.3

学习

- Started doing the labs in [Stanford CS 144: Introduction to Computer Networking](https://cs144.github.io/). I decided to just do labs and skip the course for now because I'm already reading *Computer Networking: a Top Down Approach*. This might change though, since watching course videos could be helpful in providing different perspectives and raw materials for my brain.
  - Read the checkpoint 0 instructions. Set up environments to run Ubuntu Docker container.
  - Tried stealing the header file `<linux/if_packet.h>` from Ubuntu into my local filesystem to help with IDE resolving symbols but then realized it's not worthy.
  - Had much difficulty reading the util source files in C++.
- Started learning C++ by reading *[A Tour of C++ (Third edition)](https://www.stroustrup.com/tour3.html)* by Bjarne Stroustrup, the creator of C++
  - Learned the differences between reference and pointer. Learned basic types.

阅读：

- 用1小时50分继续重新阅读《早安，怪物》中Laura的故事，详细梳理她放下心理戒备的治疗过程。

开心感激：

- 晚上八点多和老爸去一家平时少去的球馆打羽毛球，我们几乎一直都是在下午打球。这次主动做出改变很不错，宽敞的大球馆里很是热闹，有许多羽毛球俱乐部的成员在这里活动，还有不少相对业余但自得其乐的年轻人，整个环境和氛围让人愉快，让我产生了“好好学习一下基本功，锻炼一下技术，到时候可以选择适合自己的俱乐部来结识一些水平相近的球友，想想就很兴奋啊”的念头，同时也让我确定Tim Ferriss的理念很正确：试着去对生活中习以为常的行为和模式做出调整和改变，会得到很多启发和能量。这种思想对于我这种有顽固牢靠的个人体系和行为模式的人来说帮助很大，我以往总是认为自己已经做得不错了——长期坚持做时间统计和总结复盘，审视自己的生活，珍惜时间——但却依旧没有让自己觉得足够满意和认可。那么，为什么不尝试调整体系（例如不要再过度反思）呢？The system that got me here today can probably get me only this far. I need something else to keep moing.



2025.6.2

学习  Networking

- Learned about the reasoning behind sequence number for reliable data stream, and this really reminds me of the term number in the Raft consensus algorithm - perhaps designing a timestamp is highly intuitive to our humans when trying to model real-world events (in the case of networking, the event is sending a particualr packet of data).
- Learned the Go-Back-N and Selective Repeat protocols, and played with the interactive animation where I could kick off sending packets, pause to kill arbitrary packet (sent from server) and acknowledgement response (from receiver), and examine the buffer window in the sender. This is super fun!
- Learned abou the TCP segment structure and how round-trip time is dynamically updated to adapt to fluctuating network conditions.

阅读：

- 《早安，怪物》重新读Laura的故事

开心感激：

- 老妈像往常那样一大早就出门买菜买鱼买水果，拎着一个巨大的袋子和几个中小尺寸的回到家，她是如何用迷你电瓶车采购了这么大量的物资，这一直是个谜
- 感谢好友小胡推荐的视频，看到了一位优秀的父亲的培养孩子的理念和模式，受到了启发
- 感谢理发师为我剪了干净清爽的发型
- 感谢世界上有雷军这样的榜样，纯粹地自我驱动追求理想
- 小唐再次表示受到了我的激励和鼓励，近期频繁地锻炼自己去和不喜欢的人进行平静的沟通，减少了很多内耗



## 2025年5月

### week 22

I delieverd the article on assembly and registers, as I promised!



2026.2025.5.31 + 2025.6.1

创作：

- 完成了文章《打打基础 | 从翻转链表到寄存器、汇编与内存》的构思和写作
- 将今年二月份在领英上写的文章《Inside the 73-Hour Roblox Outage: A Deep Dive into Hidden Database Failures》加上中文序言，搬运到了中文博客平台上

开心感谢：

- 感谢好友晓雯赠书《建筑的复杂性与矛盾性》
- 我突然明白了为什么大学本科期间如此封闭狭隘，更加理解了我的行为模式和个人成长



2025.5.30

学习 CSAPP

- Learned about machine code and amazed by how much information is embedded in hex numbers.

  > **Assembly:** mov %edx, %eax
  >
  > **Machine code**: 89 d0
  >
  > **Opcode breakdown:**
  >
  > - 89: Opcode for MOV r/m32, r32
  > - d0: ModR/M → 11 010 000 → 11 means register-direct, 010 means source %edx, 000 means dest %eax

- Learned some basics: `movzbl (%rbx,%rax,1),%ecx` and `movb (%rbx,%rax,1), %cl` are different; PIE (position-independent executable) allocates fixed memory address (good for educating but not security) to objects; virtual memory allows different programs to use the same address like `0x6032d0`; stack frame padding before calling a function

- Found the secret phase (the last quizz) of the Bomb Lab, and solved it (a pretty simple recursion)

- Got more proficient using GDB, especially examing memory and adding breakpoints to navigate through the instructions.



2025.5.29

学习 CSAPP

- Learned how struct and union work in C language. Union is an interesting design - I like the example of using union to represent a tree node to save memory usage:

  - ```c
    typedef enum { N_LEAF, N_INTERNAL } nodetype_t;
    
    struct node_t {
    	nodetype_t type;
    	union {
    		struct {
    			struct node_t *left;
    			struct node_t *right;
    		} internal;
    		double data[2];
    	} info;
    };
    ```

- Learned the arithmetic opeartion of pointer object. Say p is a pointer of type `char *` having value p, then the expression `(int *) p+7`  computes $$p + 28$$, while `(int *) (p+7)` computes $$p + 7$$.

- Spent a lot of time on Bomb Lab's phase 6 (last one). I didn't realize I should use GDB and instead dry-ran the entire process by writing down the stack frame and keeping track of all relevant registers on my scratch paper and in my head (which is really hard). I finally figured out all the logical blocks in this phase - reading 6 numbers provided by the user, ensuring they are different from each other and all between 1 and 6 (which means they have to be from 1 to 6), putting the next pointers of a linked-list object inside the stack frame and then reversing the linked-list, and finally ensuring that the values in the linked-list are ordered desc. With GDB I was able to look at the values inside the linked-list and finally solved the problem.

- Finally set up GDB by spinning up an AWS EC2 micro Ubuntu machine. I learned the basics of GDB: Add breakpoints (`break *0x4011fb`), show all variables, check registers, and examine memory (`x/40wx 0x6032d0`). This is super fun!
  - I tried to use GDB on my M2 Macbook Air but it simply won't work due to architecture mismatch. I only realized that after trying a bunch of stuff: I tried to codesign the corresponding certificate to bypass Apple's System Integrity Protection; I tired  `lldb` and a Ubuntu Docker container.

开心感激：

- 做Bomb Lab非常专注，投入了七个半小时，题目设计和使用GDB都非常有趣



2025.5.28

学习 CSAPP

- Learned how an array consumes a few consecutive blocks of memory and we can simply use the starting address of the array plus the offset (element index multipled by the size of the element type) to locate any element inside

阅读：

- 白先勇的《树犹如此》笔触真挚，故事感人。第一个故事是他和友人王国祥相知相识的经历，他陪伴患上贫血症的友人直至生命的最后；第二个故事是他的三姐在去到美国逃离战争时患上了精神分裂，由此回到了童年时代的人格，用善良、真挚和孩童的稚气去关心和打动身边的人。

开心感激：

- 晚上自录了视频，相当全面地梳理了生活近况，对于接下来有了更清晰的目标
- 老爸陪着打了五局羽毛球（一直以来他的极限都只是四局），双方发挥表现都不错



2025.5.27

学习 CSAPP

- Finished the phase 4 and 5 of the Bomb Lab assignment
- Deeply studied an example and gained much deeper understarnding - The function call chain is `phase_6` -> `read_six_numbers` -> `stdio.sscanf`. The `sscanf`  function takes 8 arguments. I see how the last two arguments are stored at the top of stack frame, and they are actually memory addresses pointing at objects in the stack frame of previous funciton caller via instruction `mov %rsp, %rsi`, so that once `read_six_numbers` and `stdio.sscanf` finish, we can go back to the stack of function `phase_6` and find the 6 numbers just produced by the function call.
- Learned some common tricks like `shr $0x1f,%ecx` (test if the value is negative), `xor %eax, %eax` (set to zero).
- Now I have deeper understanding that each memory slot is identified by a 64-bit address (which is why each pointer object consumes 8 bytes) and holds one byte of data. Of course this is pretty fundamental but I didn't fully capture the idea.

阅读：

- 《After the falls》：了解《早安，怪物》作者Catherine Gildiner的青年成长故事

开心感激

- 学习汇编语言非常专注，投入五个半小时



2025.5.26

学习 Computer Networking

- Learned about peer-to-peer connection and BitTorrent protocol.  It's interesting to calculate the average time of receiving files and compare the performance against client-server model. It's also interesting to see how P2P simulates human community - incentize contributions and punish freeriders
- Learned basis about video streaming, `nslookup` etc.
- Learned the motivation behind Content Delivery Networks and how CDN saves money and improves user experience. Briefly looked at Netflix Open Connect
- Learned that direct TCP connection doesn't mean physically directed, but rather there's no extra layer of intermediary like proxy/relay.

阅读：

- 《早安，怪物》继续重读Danny的故事

开心感激：

- peer-to-peer file sending非常有意思！
- 写长回复支持鼓励小唐积极地在公司内部转岗到产品经理，并打消她“有手感的事要干久一点，尽量避免多次横跳”的顾虑，得到了她的积极反馈“我靠好有道理啊，每一段都很有道理”



### week 21

本周是史上第一次阅读时长突破十小时的一周，感谢《早安，怪物》这本极度优秀的作品！



2025.5.25

学习 Computer Networking

- Learned more about HTTP and DNS; Learned about SMTP

阅读：

- 《早安，怪物》：投入两个小时阅读了最后一个故事。Madeleine的经历很有趣，让我第一次意识到「不配得感」竟然可以强烈到这种程度，以至于支配一个人的生活，哪怕她十分优秀出众，也依旧发自内心地认为自己是个丑陋邪恶的怪物——来自她母亲的长期洗脑。另一个有趣的点在于作者，作为经验丰富的心理学家，却也会犯下新手级别的错误：过早透露自己知道的信息，剥夺了让对方独立自主领悟的机会。同时，作者发现，原来自己对于Madeleine和她父亲产生反移情，源于作者自己在青少年时期曾经经历的创伤，而这份伤害甚至连她本人都没有意识到。认识自我真是一生的课题。

开心感激：

- 《早安，怪物》这本书读完了 I enjoyed every minute reading it!
- 在Bilibili上看到视频讨论了一个法律案件：男女双方自主发生了两次性行为，并在事后保持聊天，女方在父母的要求选择报警，最终法院认定男方犯强奸罪而入狱三年。这个案件值得思考，女方「事前同意但事后反悔」的行为让人思考强奸罪行的定义和边界是什么、弱势群体在舆论上拥有的优势、中国社会年轻人的婚恋观以及长期的出生率会如何受到影响。



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
- 老爸老妈用心烹饪的鸭汤非常好喝



2025.5.23

学习：TiDB源代码

- 整理提交了第一份pull request来删除`logicalOptimize` 中的无效变量 `interactionRule`, 初步熟悉了TiDB Github workflow和粗略看了CI （我认为Github设计远远不如GitLab好用而人性化）
- 设置breakpoint来详细阅读 `PlanBuilder` 中的函数 `buildTableRefs`,  `buildDataSource`, `buildSelect` 等，每个函数都十分巨大（三四百行代码）而却没有清晰明确的unit test, 我对此感到很惊讶，需要深度研究一下test设计

阅读：

- 《早安，怪物》：沉浸投入两个小时阅读了Alana的故事，她所遭受的苦难和展现出的韧性令人震撼。

开心感激：

- 《早安，怪物》太精彩了！非常愉快的阅读体验
- 下午和老爸去打羽毛球，双方都有一些不错发挥不错的回合。最近几个月里，我们每隔几天就会一起打球，对于「有了搭子」这种事情我向来是很感激的。
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



## End of file

