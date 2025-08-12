## 2025年8月

8.11 周一

学习



8.10 周日

学习

- Learned about Linux cgroup, systemd and how Docker uses them.
- Read 小红书 tech blogs on how to build cloud-native infrastructure.
- Briefly read RocksDB's document on Column Family.

阅读

- 《Show Your Work》by Austin Kleon: 尽可能多地在互联网上分享自己的日常项目、进展、思考、成果和失败，战胜完美主义。

创作

- 完成了短文《Switch体感游戏是很棒的启蒙教育》的创作，记录了我对于表妹在家里玩Switch游戏的观察和思考。

开心感激

- 对浏览器的收藏夹进行了不少整理，迈出了建立秩序的重要一步。我早就意识到了大量囤积任务并且每天都一动不动会对我的精神健康带来负面影响，给我一种生活停滞不前、一成不变的压抑感，我会解决这个问题的！
- 综合时长久违地恢复到了9个小时的水平，今天过得很充实！
- 我的行动力很强，吃早餐的时候想到了写作素材，中午就立刻着手写作并发布了。
- 看了演唱会现场视频 Luke Combs & Alex Warren - Ordinary (Live at Lollapalooza) 被触动落泪，感谢音乐让这个世界更美好。



## 2025年7月

7.30

开心感激

- 探索出了在电脑上进行语言输入文字的模式，感觉具有非常大的潜力！我很期待！



7.29

学习

- Sorted out the design of components in CS144: `TCPSender` and `TCPReceiver` make up the `TCPPeer`, which gets initialized inside `TCPMinnowSocket` , which combines with `TCPOverIPv4OverTunFdAdapter` to form the `TCPOverIPv4MinnowSocket`. Once tricky part to understanding the full design is we need to realize that a connected machine is both a sender and receiver, so both `TCPSender::receive` and `TCPReceiver::receive` need to run when receiving an incoming packet. This duality can get pretty confusing.
- Learned TunTap network interfaces and how they help bypass the kernel's IP/TCP stack and use my own TCP implementation, but I haven't fully figured out the counterpart to the socket APIs `listen`, `accept` and `connect`. Also learned how to unpack an IP packet to examine the TCP packet inside.
- Learned how to use macro to create a customized debug logger in C++ to print out the current timestamp and caller function name. The long macro looks a bit ugly but I'm getting used to it.

阅读

- 《*Tools of Titans*》：Instead of trying to be the best in the world at a certain area, an easier approach is become top 25% in 2 to 3 areas and then find the unique combination/path of these areas.

 开心感激

- 感谢羽毛球教练对我保持耐心，虽然我们的表达方式和说话偏好有着不小区别，但是我意识到我不必要太在乎这个差别，而是要尽可能地从对方身上学到好的东西。另外我又一次认识到了自己过于娇惯，练习后场高远球搭配前场网前推球很容易就感到疲惫和心肺功能跟不上，匆忙结束后进行大腿拉伸时又觉得实在太痛了根本受不了，没有一丁点儿咬牙坚持的韧性，我发现这和我在日常生活中低强度学习和对待自己过于轻松随意，其实是一脉相承的行为模式。我需要改变。



7.28

学习

- Learned the CS144's design of `TCPPeer::receive` and figured out the details of all 3 events TCPPeer will listen to. Drew a diagram to make it easier to follow the flow. Learned more about system's `POLLIN`/`POLLOUT`.
- Learned RocksDB's `Status` design and a few simple unit tests in `db/db_test.cc`.

阅读

- 《*Tools of Titans*》：Tim Ferriss decided to create his own two-year MBA program by spending \$120K to invest 6 to 12 startups. Scott Adams shares the difference between systems and goals.

开心感激

- 给爸妈买了一床清凉散热的床垫，还各买了一只符合人体工学的枕头，我感觉很满足。
- 上午读过书之后开始立刻实践书中的理念，在草稿本上写下了15遍 “我会打造出顶尖的个人系统”，希望能借此强化内心信念。



### week 30



7.26

学习

- Learned more basics about C++: universal referrencing; keywords `requires`, `constexpr`, `default`, `delete`, `decltype`; examples where implicit type casting causes problem.
- Read networking RFC 7234 on caching and understood how cache freshness is achieved.
- Learned why separating `listen` and `accept` as two syscalls.
- Used `tcpdump` to capture some real-world packets to examine the content bytes to understand the IPv4 datagram heade, TCP header and the payload.

阅读

- 《*Tools of Titans*》 by Tim Ferriss: 本书的意义和使用方案，清晨写journal的意义，对Reid Hoffman和Peter Thiel的采访提炼。



7.25

学习

- Learned thread pool and made my CSAPP proxy server able to handle concurrent requests.

阅读

- 《仿制药的真相》by Katherine Eban (*Bottle of Lies: The Inside Story of the Generic Drug Boom*的中文版) 开启阅读。



7.24

学习 CSAPP

- Read the buffered and unbuffered versions of the robust I/O API and got better understanding. Read through the full list of networking syscalls during `strace -e trace=network curl -v http://...` to gain more fluency in networking.
- Finished the part 1 of proxy lab by setting up the proxy server and I was able to run `curl --proxy http://localhost:15214 -v http://localhost:15213/home.html` to fetch the data I need.

阅读

- 《Useful, Not True》 by Derek Sivers: 一个观点、评价、理念等是否正确并不重要，它取决于语境中具体人物的成长环境、视角和主观感知，生活中的绝大多数事物（甚至包括一些科学观点）都是主观的。我们不必要在乎是否正确，只需要在乎它们是否对我们有帮助即可。



7.23

学习 

- CSAPP
  - Read through the source code of tiny web server in the  proxy lab and got more familia with socket programing APIs.
- CS144
  - Figured out how the bidirectional stream copy works, which consists of 4 different listening events: STDIN -> outbound bytestream -> `socket.write()` and `socket.read()` -> inbound bytestream -> STDOUT.
  - Once again learned what's lvalue/rvalue in C++ and that `std::move` produces a rvalue. Also learned about 4 kinds of object type casting.

阅读

- 《成长的边界》：更多的跨领域优质人类案例分享。

开心感激

- 晚上爸妈分享回顾了他们小时候和青年时代的生活艰辛，一罐萝卜干要吃一整周，除了粥以外没有任何的食物，在冬天甚至要面临没水喝的苦境。难以想象他们究竟是怎么顽强地存活下来的。



2025.7.22

学习

- Learn `poll` system call and its role in event-driven programing.
- Read other students' design of the malloc allocator and also briefly looked at the GNU malloc.

阅读

- 《最好的告别》：见到了更人性化的养老院设计——让老年人们像是室友般共同生活在同一间公寓里，彼此都有各自的独立房间，房间里有电视，大家可以按照自己的喜好来作息。

找工

- 逛了上海蚂蚁集团近一个月的所有相关岗位，大致可以划分为如下几个我可以尝试的方向：存储 (RocksDB, Hbase, Raft, etcd, Redis); 云原生 (Kubernetes, CRD operator, Terraform, AWS, Golang);  数据仓库 (Spark, Flink, Dimensional Modeling, ETL); 计算引擎 (Clickhouse, Doris, C++); 后端开发 (Java, Sprintboot, Kafka, Redis, Middleware). 我目前最渴望做的仍旧是存储/数据库开发方向，但也并非顽固不变，能接触到infra的后端开发也是可以考虑的。

开心感激：

- 在网上读到了优秀[本科生蔡思涤](https://littlecsd.net/)的技术博客记录分享了CSAPP的学习以及其他内容，受到了很强烈的冲击，感谢他的优质内容予以我痛苦让我清醒过来。



2025.7.21

学习

- Learned pthreads API like `pthread_create`, `pthread_join`, etc with great example in man7 org. I notice that I've seen this before in CSAPP but I need hands-on coding to get trully familiar. 
- Learned C++ lambda with example in CS144 bidirectional stream copy. Learned more about `size_t`.

阅读

- 《最好的告别》：Assisted Living养老院模式的后期失败；Bill Thomas在疗养院中引进猫狗鸟等动物帮助老年人们对抗三大瘟疫：厌倦感、孤独感和无助感



### week 29



2025.7.18

学习 CSAPP malloc lab

- Finished implementing `realloc` . I tried to handle the access pattern to achieve good utilization performance but again I realized that I can't really beat every access pattern.
- Fixed two bugs
  - Some free blocks ended up not belonging to any freelist. Turns out I didn't properly release a free block before using it because of my poor design of functions' interfaces. I didn't distinguish helper functions, chain functions (function B must be called after function A), and entrypoint (public) functions in my code.
  - The function to find the target freelist is too overloaded, shared by different logic.

阅读

- 《The Push》: Tommy met Becca, his future wife, and Kevin, his future climbing partner on the El Cap.

开心感激

- 去看了今天上映的《罗小黑战记2》大电影，期待了许久，虽然不及预期，但还是很感激。



2025.7.17

学习 CSAPP malloc lab

- Introduced factory meta nodes for making more meta nodes and freelist heads to further improve space utilization. Automatically remove all empty freelists except the factory. Improved the coalescing logic by avoiding having to add a new block to freelist and then immediately remove it.
- Fixed three bugs: I should always wipe out the payload before releasing a free block; I should make `mm_init` function idempotent so that it can be called multiple times through the lifecycle of the program; I mistook size class as block size but it's actually payload size - I added more comments and better naming to address the issue.
- Achieved pretty good performance (91% utilization and 100% throughput). I tried to further improve utilization by introducing randomness into the number of bytes to extend the heap when requesting more memory, but I realized that I can't really improve consistently any more because at the end of the day the utilization depends on the usuage pattern and downstream users can always devise a pattern to beat my design.

创作

- 《罗小黑战记》是我很喜欢的国产动漫，给我带来过很多的治愈、抚慰和支持，我写了篇《写在罗小黑2上映前》搜集了剧集中的美好瞬间。

开心感激

- 我写的malloc分配器的性能不错！
- 和很要好但已经一年没联系的朋友一翔catch up生活的近况, 感到很幸福。



2025.7.16

学习

- CS144 check3
  - Fixed a lot of bugs: `TCPSender::push` should respect the window size and current availability, it should also continue sending messages until either there's no data left in the upstream application or no room left in the downstream TCP receiver; `TCPSender::receive` should have the similar loop to continue acknowledging outstanding messages until the latest ack number isn't enough to cover the message;  `TCPSender::retransmit` shouldn't run when the timer is not running (no outstanding messages); properly add SYN and FIN flags by introducing status UNSENT/SENT/RECEIVED; only reset the timer when there's new message acknowledged (not all ACK is meaningful).
  - Handled a few special cases: window size is 0 (don't add backoff to the timer); retransmit a FIN flag only message.
  - Traced how strings are moved along: `ByteStreamReader::peek` returns a `string_view` and the `TCPSenderMessage.payload` is `string` so it does really matter when I pop the buffer in the `ByteStream` to avoid use-after-free.
- CSAPP malloc lab
  - Observed the logs of handling large batches of memory requests and noticed a lot of the freelists in my design are empty and thus wasting space and time (making traversing the linked list much slower).

开心感激

- 我一直以来都是穿篮球鞋去打羽毛球，今天购买了专业羽毛球鞋Victor S82三代，很明显地感受到脚下步伐轻盈了许多，有了更多的支撑，很开心！



2025.7.15

学习 CS144 check3

- Implemented the `push` and `receive`  functions of the `TCPSender`, and was able to pass certain tests.
- I struggled with the fact that the SYN and FIN flags in the TCP message don't show up in the payload but still count as message bytes. My `receive` function is flawed because it assumes it should only remove one message but in fact the acknowledgment message from the TCP receiver might ack a bunch of messages all at once, and thus I would need to introduce a while loop.

阅读

- 《The Push》by Tommy Caldwell: I read how Tommy met Jim Collins, got divorced with his partner Beth.
  -  Jim (my personal hero, who also used to be a great climber, also raised in Colorado) is naturally curious about everything and started doing business research, and I'm surprised that Tommy got so focused on climbing that he basically didn't think about anything else - like connecting different disciplines, learning from different inspiring people, reflecting on his own target setting and technique growth. He was so vulnerable and suffered a lot at his marriage. I think that's because [1] he didn't learn how to properly express ideas and feelings in intimate relationship; [2] he basically didn't have any close friend except Beth; [3] he didn't seek help, feedback and support from others; [4] he was too naively optimistic to think that the problem would **soon be gone** and didn't have the courage to face the brutal truth that there were serious problems; [5] I suspected that he didn't do much reading daily and didn't learn outside of climbing.
- 《大萧条》by Ben Bernanke (*Essays on the Great Depression*的中文译本)：读了大萧条期间的就业、每周工作小时数和收入的计量经济学论文，我发现我对这样简单的线性计量模型和天真的模型假设感到惊讶，现实世界是如此复杂（显然各个因素都是相互交互的，并且无差异效用曲线根本不存在，完全无视了人类心理学），我发自内心地觉得这所谓模型和研究只是天真幼稚的自娱自乐罢了，但是实际上Bernanke作为美联储主席对应对2008年金融危机做出了很大贡献，我还未能联系起来他是怎么做到的。

开心感激

- 和爸妈一起看了纪录片《猎捕》 第二集，介绍北极圈生物的捕食——北极熊捕食海豹，北极狼捕食北极兔和麝牛，北极狐捕食崖海鸦。非常精彩！我看到了动物们如何在生存条件最恶劣的地区寻求生机，它们生存的模式和烦恼，和人类是如此的不同，我学到了许多。



2025.7.14

阅读

- 《最好的告别》by Atul Gawande (*Being Mortal: Medicine and What Matters in the End*的中文译本): 介绍了大多数人习惯让老年人在养老院或者治疗室度过。



### week 28

我又一次犯下了和上周同样的错误，只进行一次每日汇报，大致有三个原因，其一是我潜意识里对其不够重视，觉得是否记录汇报并不十分重要，并不会影响到我日常表现（实际上，它虽然不会立刻展现出来，但却是会逐步侵蚀我的精气神）；其二是我白天的消耗太大，以至于晚上已经没有力气和情绪去进行记录了，这个需要刻意培养才行；其三是我没有容错机制，我只允许自己在晚上进行记录汇报，如果连续两天错过时间窗口，整个人就会开始放弃——我需要确保自己有足够稳定的基准线才行，如果晚上没能记录，那么第二天的白天必须及时补充，绝对不能落下进度。

相比之下，本周更为重大的错误是，我**又一次地**只进行单一学习活动，我连续多日专注沉浸地投入于malloc lab之中，完全没有接触networking内容。我生活中只剩下computer systems了，哪怕写lab时十分兴奋亢奋，也不足以应对傍晚结束后的疲惫和精力垮掉。单一任务无论如何都是行不通的啊！我的生活近乎停滞（这个关键词很熟悉吧，我这些年来在美国期间常常有这种感受啊）了，只剩下这一个单一启动点（也称之为瓶颈）了，CS144 checkpoint 3已经拖了几乎一周，整理回顾Notion文档这项任务也是，『晚上写report回顾今日』这项目标也因为自己过于疲惫且晚上没有时间了而被完全搁置了，连前些天在坚持做的拉肩膀康复也被完全遗忘了，可恶啊！又陷入到了那种“日子一天天过去，感觉自己浑浑噩噩地用机械直觉来写代码”的糟糕状态。这样to-do list跟从前那种「不用任何当日安排，每天只管看准一个任务使劲莽，把所有时间都投进去就行，拆解milestone和预估时长安排项目啥的我不管我不会」的老旧模式在本质上没有区别！虽然malloc的确很有挑战很有意思，但not special enough to break the rules! 我完全高估了这项任务的价值。

看来我还是没能把**「绝对禁止一天只做一件主任务」**的新认知给贯彻落实到底。

其实我现在这种渴望尽快把malloc给做完的心态，和当初在美国工作时每天盼着把某个project尽快完成是完全一样的，整个人变得狭隘，关注点变窄，日子重复单调枯燥损害大脑和无意识，感受不到那种生活丰富多彩、头脑活跃时的持久幸福。我知道我在沉浸写lab的时候希望能够再多些一会儿，但是我现在明白了，我必须自己强制限时才行。不用担心自己的专注和热情散掉了浪费了，切换到Networking任务之后，也能够迅速地找到快感（如果没有，要么是因为自己浮躁了，要么是因为自己挑选的学习着手点不对），所以啊，我这是通过切换项目来保持自己的健康愉悦和专注啊！写了六个小时的malloc之后我都想不起来自己做过了什么，而如果malloc/networking分别做三个小时，那么我可以清楚地回溯追溯出思考的框架和逻辑链路，清晰地知道自己在着手哪一步，哪个环节可以改善，并且在闲暇时间里大脑还会自动加工进行沉淀提炼，而不会像现在这样直接抽离出来彻底罢工不思考了。



2025.7.13

学习 CSAPP - malloc lab

- Fixed the error of forgetting to zero-out the payload of a newly free block.

阅读

- 《诺兰变奏曲》：继续介绍《盗梦空间》和《蝙蝠侠 - 黑暗骑士崛起》的创作
- 《早安，怪物》：梳理书中内容进行写作

创作

- 艰难地寻找切入角度和叙事手法，综合介绍了Laura, Danny, Alana, 以及作者Catherine本人的案例分析，完成发布文章《精读系列(五) | 梦、无意识与防御机制》



2025.7.12

创作

- 完成发布了文章《精读系列(四) | 当我开始与无意识沟通》
- 梳理归纳《早安，怪物》书中的对于梦境和无意识和描写和案例分析。

阅读

- 《诺兰变奏曲》by Tom Shone (*The Nolan Variations: The Movies, Mysteries, and Marvels of Christopher Nolan*的中文译本)：介绍了经典电影《蝙蝠侠 - 黑暗骑士》和《盗梦空间》的创作过程。

开心感激

- 晚上和爸妈在电视上看纪录片《风味人间》介绍小麦、大麦和青稞的故事和食物制作，很幸福愉悦。



2025.7.11

学习 CSAPP - malloc lab

- Understood how to handle alignment - I was able to guarantee that all blocks and the returned result of `malloc`/`free` must be 8-bytes aligned.
- Implemented the logic of coalescing multiple free blocks. Redesigned the logic of traversing the linked list to find the target node.

阅读

- 《集异璧》by Douglas Hofstadter (*Gödel, Escher, Bach: an Eternal Golden Braid*的中文译本)：递归在音乐、绘图、数学、物理中的体现。



2025.7.10

学习 CSAPP - malloc lab

- Implemented the mechanism of searching for freelist, allocating a free block given an appropriate freelist head ndoe, splitting a large chunk into an allocated one and a free one.
- Solved the circular dependency issue by  refactoring the function that directly adds a new top level block node.
- Fixed the error during fetching the block size and flag from the block header/footer.

阅读

- 《早安，怪物》：回顾Madeline经历的创伤和治疗。

创作

- 梳理回顾我近期尝试与无意识沟通的努力。

开心感激

- 晚上重温经典曲目，被旋律和歌词打动哭了 “愿这世界如童话，抱着想象实现它。就凭摘星的手臂，为地球每夜放烟花。就算世界无童话，放下包袱完成它。”
- 在网上学习了羽毛球的4种应对不同场合的后场正手进攻步伐，系统学习实战的感觉太棒了！



2025.7.9

学习 CSAPP - dynamic storage allocation

- Read through the end-to-end simple heap allocator with implicit free list (whose operations take linear time). Digged into the components of each block: header, payload, and optional footer.
- Started doing the malloc lab and finished the C macros for handling raw pointer arithmetic. And I had a rough idea (walked through the details on paper) of how to implement the segregated fit free list design.

阅读

- 《发现的乐趣》：费曼分享美国挑战者号航天飞船事实调查过程。
- 《成长的边界》：作者先是分享了美国各大商学院将挑战者号事故作为教学案例，启发学生们要积极寻找更多的材料进行决策，随后又否定了商学院的这套理论，认为NASA的实际错误在于过于强调量化决策而忽视了定性分析和因果推断。
- 我通过交叉比对这两份文稿来研究人们是如何研究同一个课题的，思维的堆叠很有趣。
- 《早安，怪物》：重新回顾和梳理总结书中对于梦境和潜意识的描写，为我本周的写作做准备。

开心感激

- 晚上陪爸妈看电视体育节目。



2025.7.8

学习 CSAPP -  virtual memory and dynamic storage allocation

- Learned translation lookaside buffer (TLB) and how it helps with performance. Notice that both it and the L1 cache are on the CPU but TLB has performance advantage.
- Learned the end-to-end process of address translation: given a virtual memory address, divide it into virtual page number (VPN) and virtual page offset (VPO, which is equal to the physical page offset, so I'd like to just call them page offset), further divide the VPN into TLB tag and TLB index, which are used to identify whether there's a TLB cache hit. Combine the fetched physical page number and page offset to get the physical address, and divide it into cache tag, cache index and cache block offset to check against the L1/L2/L3 cache and main memory.
- Learned how malloc/free works and the heap memory allocator's policies on placement (first-fit, next-fit, best-fit), splitting and coalescing multiple free blocks.

阅读

- 《成长的边界》广泛接触多个领域和知识面的成员们组成的团队对于各类事件的预测准确率很高。

开心感激

- 雷暴大雨，让我感到很舒适很开心，下雨天总能给我带来灵性。
- 晚上睡觉前和老妈在客厅电视上看一期介绍浙江跳跳鱼和福建坛紫菜的饮食节目，很幸福的亲子时光。



2025.7.7

学习

- Computer systems
  - Went through the full list of `errno` and studied some popular ones like `EPERM`, `EAGAIN`, `EMFILE` , etc. and their impact on production systems. Learned more about Linux manual and system calls (e.g. atomicity and retry on `EINTR`).
- Networking
  - Worked on TCP sender of the lab checkpoint 3.

阅读

- 《成长的边界》：通用型人才；任天堂早期在计算器上开发游戏，用新的视角来看待旧的工具；3M公司开发光学薄膜。我意识到达尔文的做事模式是我十分欣赏并想要去模仿的：

> 只有在“适合他这样的科学通才去攻关的实验”出现时，达尔文才会亲自做实验。对于其他的东西，达尔文依靠的是与他人通信，他的风格和杰西里·赛斯一致。达尔文总是能在数个项目中游刃有余，格鲁伯称之为“达尔文的项目网络”。他至少有231位科学方面的笔友，从蠕虫到性选择，这些笔友按照他的兴趣可以大致分为13个大类。他接二连三地向这些笔友提问，然后再把这些回信中的信息裁剪下来，贴在自己的笔记本上，“笔记本里的思想看似混乱地相互碰撞”。当他的笔记本太过庞杂时，他就撕下几页，按照自己询问的主题进行归档。光是种子实验，他就和法国、南非、美国、亚速尔群岛、牙买加和挪威的地质学家、植物学家、鸟类学家和贝壳学家进行了书信来往，更不用说一些业余的博物学家和碰巧认识的园丁了。正如格鲁伯所描述的那样，创新者的活动“在旁观者看来，像一个令人困惑的混合体”，但是他或她能够把每个活动对应到正在进行的具体项目中。格鲁伯总结道：“从某种角度看，查尔斯·达尔文最伟大的作品是对他人先收集到的事实做了解释性汇编。”他是横向思考的整合者。

开心感激

- 晚上回到卧室突然发现顶灯坏了，老爸去家附近的五金店买来36瓦的灯管，不过我卧室里的灯具并不是那种带有灯泡螺纹的设计，需要把拆除九只螺丝并且解开铜线缠绕后才能卸下来。难度不大，但这种亲子时光很宝贵。



### week 27

本周的表现很不令人满意，原因其一是近乎报复式地花了好几个小时去重温《罗小黑战记》，导致整个人处于很松垮的状态；其二是整个人不是很清醒，一周的时间仿佛一眨眼就过去了；其三是我无意中几乎摒弃了daily report的routine, 只在周四这天下午一口气补充了本周前三天的报告，此后就没有再写report了，我的本意是将写报告反思的时间调整至每天晚上，但是却发现每天晚上都有大量任务需要完成，根本挤不出时间（当然也是因为优先级规划不到位）。

整个人浑浑噩噩的，既没有坚持执行最新的作息体系，也没有带着激情去面对日常学习——虽然我还是出于习惯和本能地在学习。录视频本该是能够帮助自己清醒过来的，但是本周只匆匆录了十分钟便结束了，

简单而言便是，我并没有带着清醒的意识去朝着我理想中的方向前进。

tested the wall

- 我意识到我这些年来进行每周的时间统计时总是在草稿纸上进行手算，是相当机械重复的步骤。虽然我在很早以前就写了Python程序来进行每月时间统计的自动化，但是在每周维度上还是习惯性手算。于是我在原有script上进行拓展和优化，实现了每天登记活动时间之后自动统计出本周、本月的总产出，相当方便。
- 开始尝试在本子上写下脑海中随机产生的impulse和各种联想回忆，训练自己抵抗随机冲动的能力。
- 购买了《罗小黑战记》的电影画册——内容包括人物造型设计、分镜稿、场景设计、画风探索、三维取景、后期合成制作等等，是非常精美、让人爱不释手的艺术品。我的日常生活几乎是百分百以电脑为中心展开的，我一直认为我需要给生活中增添纯纸质材料，来帮助自己偶尔完全切断电子设备的连接，静下心来。



2025.7.6

学习

- Read some of the zsh source code like signal handler. Attached `strace` to a running zsh session to identify all syscalls involved.

写作

- 整理我在阅读《Beyond Entrepreneurship 2.0》过程的思考感悟，完成了读书笔记《Netflix老板每年都会重温的创业书》，我很满意！

阅读

- 《成长的边界》：梵高在成为画家之前的各种探索尝试；西点军校没能在训练营结束后留下人才的原因分析；Frances Hesselbein起初只是热衷帮助他人，摸索出了自己的职业路径，被Peter Drucker称赞为最优秀的CEO; InnoCentive向社会公众发布专业难题，通过寻求专业之外的局外人的创意和思路来解决难题；Jill Viles - How a woman whose muscles disappeared discovered she shared a disease with a muscle-bound Olympic medalist.



2025.7.5

学习

- CSAPP
  - Read the malloc lab requirements and read some of stuff about virtual memory in the textbook.
- Networking
  - Implemented the TCP receiver and thus finished the checkpoint 2 lab.

阅读

- 《How to ADHD》: For those who don't have ADHD, how to support those who do



2025.7.4

学习

- Finished the `Wrap32` implementation in CS144 checkpoint 2.
- Learned basics about CMake, including commands like `add_dependencies`, `add_library`, `add_custom_target` , `target_link_libraries` and variables like `CMAKE_BINARY_DIR`, `CMAKE_CTEST_COMMAND`.

阅读

- 《成长的边界》：学习任务需要有适当的认知难度。
- 《The Art of Impossible》: Train when you're at your worst



2025.7.3

学习：

- CSAPP
  - Reviewed the finished tiny shell and consolidated my learnings.
- Networking
  - Read fellow engineers' implementations of the reassembler.

阅读

- 《成长的边界》：某孤儿院里的孩子们通过广泛接触各种乐器，最终被培养成了杰出的音乐家。



2025.7.2

学习 CSAPP tiny shell lab

- Read the text book more once. Tried 3 ways of running nested shell programs - [1] running zsh inside my tsh; [2] running my tsh inside zsh; [3] running another tsh inside my tsh - to learn about foreground process group, who gets the signals and stdin, etc. 
- Refactored my code to make a separate function `babysit_foreground_job` to wait for a foreground running job to finish - it can be either running for the first time or bring back to life by the `fg` command.
- Matched all expected outputs and finished the entire shell lab.



2025.7.1

阅读

- 《成长的边界》（《Range: Why Generalists Triumph in a Specialized World》by David Epstein的中文版）:介绍了Tiger Woods和Roger Federer两种截然不同的成长和训练模式，前者是很早的时候就选定一个子方向开始训练，后者是广泛尝试不同兴趣后再做决定。我喜欢这种对比研究方式。

开心感激

- 回顾2024年的年度总结时发现自己正在十分显著地有效地改变自己，远远超出年初时的预期，进步和变好的感觉真是太棒了！

  - > 在我众多的缺点弱点中，「不懂得做规划安排」给我带来过最多的创伤。一直以来，我都是个自由散漫的人，纯粹受情绪和注意力驱动，既可以沉浸式连续写代码几个小时，又可以专注地熬夜刷视频。坚持写日记这么多年，我充分剖析了自己的行为模式，我已经写不出什么新鲜新颖的反思和观点了。我究竟还能不能改变自己？当我说“我喜欢挑战困难的事情”时，我到底知不知道自己在说什么？这些问题要留给2025年的我来回答了。

- 重温了国产动漫《罗小黑战记》，再一次被这一系列温暖治愈的故事和人物打动，感谢制作团队为这个世界带来了这样的美好。



2025.6.30

学习 CS144

- Got more hands on with C++'s `std::map` and implemented the workflow of merging multiple intervals of strings into a larger one. Studied the expected behavior of adding segment of new data, and I finally finished lab checkpoint 1 passing all test cases.

阅读

- 《After the falls》Catherine tried to fit into the post-moving daily life and find her way to learn how to make friends (especially female ones, since her only friends so far have been her dad and the employee Roy who worked in dad's pharmacy store) with teenagers of her age. She was talking to a senior grade boy and her dad  mistakenly thought she was flirting with him and got furious - the first time he actually got angry with her. They started a cold war, mostly due to misunderstanding and lack of communication. I'm surprised that a well-educated and well-tempered man like her dad would end up using violent communication and hurting the relationship with his daughter.

开心感激

- 老妈尝试了全新的菜品——菠萝炒瘦肉，非常好吃！



## 2025年6月

### week 26

tested the walls

- 我在周日上午意识到，如果把每天的运动锻炼时间从晚上调整到下午，那么我便可以在夜晚拥有更完整大块的专注时间，并且下午运动过后一定会及时地结束和洗澡，迅速地完成状态切换，而不会时不时地陷入到过渡期间的时间黑洞中。下周可以好好实践下这个新作息。
- 我还是没能有效地改变自己的坏习惯，每天早上起床后总是会进入到思维漫游打发时间的状态里，做着一些无关紧要的事情。我会继续努力的，建立起真正适合自己的routine和模式。

生活的阻碍

- 肠胃很不舒服，周二和周三的半夜醒来拉肚子，周四周五上床后感受到明显的不适，占据了注意力难以入睡。
- 个人体系不太稳定，容错率较低，如果一天的开局没有按照理想情况展开，或者发生了一些突发状况，个人状态就会受到很大的影响，往往是注意力和脑力迅速地被消耗殆尽，容易陷入到打发时间的无所事事之中。



2025.6.29 Sunday

学习

- CSAPP Tiny Shell lab
  - Properly used a spin loop and `sigsuspend` (which handles races)  in the main evaluation call to wait for the foreground child process to finish. Gained deeper understandings of the signal related syscalls like `sigaddset`, `sigfillset`, `sigprocmask` (this one could be used as mutex lock to protect global variables).
  - Properly handle the running/maintaining of foreground/background jobs. Realized the importance of process group as the foundation of the process handling mechanism. There's still stuff missing in managing the processes.
- CS144 checkpoint 1
  - Realized I should use a sorted map to keep merging time slice intervals.

阅读

- 《The mountain is you》接触到一个十分有趣的观点：大脑天然地就渴望寻求挑战和困难。

  - > The human mind is something called antifragile, which means that it actually gets better with adversity. Like a rock that becomes a diamond under pressure or an immune system that strengthens after repeated exposure to germs, the mind requires stimulation in the form of a challenge. If you deny and reject any kind of real challenge in your life, your brain will compensate by creating a problem to overcome. Except this time, there won’t be any reward at the end. It will just be you battling you for the rest of your life. 

开心感激

- **晚上录了一个小时的视频，非常开心！我惊喜地发现，我竟然可以通过和自己对话聊天，来收获类似于和高质量朋友进行深度聊天的巨大兴奋和幸福感**。我明白我就是喜欢有intellectual challenges冲击碰撞，能够充分表达和展示自己（说白了就是喜欢显摆自己的优秀哈哈，以及the joy of talking现象真是十分常见），渴望被看见被理解——而我本人显然是这个世界上最了解自己的人之一，因此可以全盘接纳自己，这种百分百坦诚的接纳很打动我。我看到自己笑得很纯粹，我好喜欢自己啊，没想到居然不需要朋友在身边也能实现这么优质的人际互动爽感！并且在视频里看着自己真的是好有亲和力啊，显得人畜无害很真诚很有感染力啊！喜欢！越发期待今后创业来把这个能量场带来我的伙伴们了，一起搭建一个属于我们这样的理想主义、长期主义、乐观主义者的美好社区。
- 昨天晚上运动过后没有立刻去洗澡，而是陷入了老毛病——回到卧室里打发时间看视频。我今天仔细分析研究了我的心理——我当然明白可以借助搭建系统来帮助自己减少自残式的时间黑洞，但是我还想知道，这是我的潜意识试图在与我沟通（我为什么会「想要」去刷视频打发下时间呢，是它感受到被压迫被支配了么），还是单纯的坏习惯罢了。思考过后终于明白了我的生活缺乏丰富度：一方面是，我每天的内容充斥了太多的文本，虽然我极其喜欢代码、读书和查看高质量post帖子，但那都是同一类范式啊；另一方面是，我日常生活没有足够的休息（注意，虽然我有大量的时间在思考、消化和吸收，但那并不是对大脑而言足够的休息），我需要切换领域和范式！我的这个低效休息有点像是一些低能量人会有的：直接倒头睡觉，shutdown关机。
  - 我终于明白了，我的大脑和无意识真的是为了我好啊，一心一意地守候我，它没法直接告诉我通知我，它没有面部表情和说话语气，但我可以从我的行为和内心感受来理解它想要传达的信息，根据我的主观感受和organic天然有机程度来判断我执行的度量是否合适。我突然与自己的大脑和身体讲和了，我再也不想对我的身体施加愤怒和沮丧了。



2025.6.28 Saturday

学习

- CSAPP Tiny Shell lab
  - Learned more about syscalls, `execve` and `fork`, races when making syscalls. Implemented signal handler `sigchld_handler`. Implemented searching from env `PATH` to locate the target binary executable file and then run it. Enjoyed using `strace` even more.
- CS144 checkpoint 1
  - Read the test cases to understand the logic and workflow of the reassembler and think about good data structure for it.

阅读

- 《Elon Musk》Justine, X.com and PayPal - it's good to see Peter Thiel and Max Levchin here now that I've read the book *Zero to One*; Day-1 of SpaceX and the hiring of Tom Mueller.



2025.6.27 Friday

学习 CS144

- Improved the in-memory byte stream and finally finished checkpoint 0. I made a big mistake - I misunderstood the requirement! The `peek` function should return the next batch of bytes in the buffer, not all the bytes remaining in the buffer. So previously I spent a lot of time thinking about how to carefully craft a ring buffer to avoid copying two continuous chunks of `std::string_view` (although this kind of learning experience is useful for my growing). I corrected my error by using a queue to store the batches of input strings, instead of  a deque of all chars currently in memory.
- As a side-effect, I learned about C++'s left/right values and `std::move` stuff.

阅读：

- 《Elon Musk》by Walter Isaacson：我去年和前年读到了Chapter 82:  The Takeover - Twitter, Thursday, October 27, 2022 已经接近读完这本很厚的书了，但是我不想这样囫囵吞枣，不想浪费这本精彩的作品，于是我决定从Chapter 8 Penn - Philadelphia, 1992–1994开始重新阅读来尝试挖掘出更多内容。今天读了Elon本科期间在硅谷的summer intern经历以及创办Zip2收获人生第一桶金的故事，有不少感受，其中最强烈的是再次意识到了自己这些年浪费了大量的时间和生命，对于自己的自由散漫太过于纵容——好消息是我现在已经在着手战胜我的弱点了。



2025.6.26

阅读：

- 《BE 2.0》: Measuring, appreciating, respect. "There's no secret in running a business" 我读完了这本书，并且回过头再读了一遍开篇章节所强调的first who原则。我感到我收获了不少启发，对于未来创办企业、打造符合自己核心价值体系的圈层有了更多信心，我想要写一篇读后感来提炼我的学习感悟。

创作：

- 终于完成了《黑客入门 | 用ROP和shellcode攻击SolarWinds Serv-U SSH漏洞》写作！

开心感激：

- 好友Noco分享说我前些天写的文章《筋膜枪，电推剪，和爸妈生活的日子》很打动她，文章的真情流露和细腻细节有种抚平内心褶皱的感觉。Noco是爷爷奶奶带大的，爸妈常年在外地工作，她说现在格外珍惜和家人相处的时间。感谢我的朋友，感谢对于我写作和观察生活的支持。



2025.6.25

学习

- Continued digging deep into the SolarWinds Serv-U FTP vulnerability detailed reports. Finally understood where does the injected shellcode lives, the relationship between the buffer and the `cipher_data` structure, the reason why the huge payload of ROP chain and shellcode got sent to the Serv-U server only requesting 0x108 bytes of data read for heap spraying and why send the huge paylad one last time.
  - Read a report on this vulnerability by another hacker and I realized that there're usually multiple ways/styles to attack the same systems.
- Handled some boring engineering setup issues - my EC2 machine in Singapore suddenly became extremely slow and lagging for no reason (I've ruled out the possibility of networking issue, mostly), so I had to set up a new EC2 machine in Tokyo. Also set up my IDE CLion to allow doing remote development via SSH.

阅读：

- 《BE 2.0》: hiring, inculturation, training, goal setting

开心感激：

- 看了优质视频《非洲的切格瓦拉是谁》了解到 Thomas Sankara的英雄事迹，感谢世界上有这样的理想主义的反抗者，感谢博主「小约翰可汗」的精心制作让我们了解到Burkina Faso这个非洲小国。在Sankara被刺杀后的三十多年里，人们仍然在怀念和纪念他，这让我无比感动。



2025.6.24

阅读：

- 《BE 2.0》：execution, deadlines, SMaC (Specific, Methodical, and Consistent) 这个让我想起了《清单革命》带来的启示——在复杂系统采用设定好的SOP和清单check-list可以有效避免常见的低级错误模式。
- 在读到 If you can create an atmosphere where people are dependent on each other—where people think, “I can’t let these people down”—you’ll get extraordinary performance 这句话时回想起了《Good to Great》最后一章节中的故事，于是重新阅读了一遍。

创作：

- 受阅读的启发，创作了文章《Why Greatness? 为什么要追求做到更好？》来记录两个重大结论
  - 实现greatness其实并不比做到good更为困难，它其实并不需要承受更多的痛苦和付出更大的代价。
  - 如果我们对于正在做的事情由衷地感兴趣，发自内心地在乎，享受其中，从中找到了意义感和成就感，那我们天然地就会想去把这件事情做好。


开心感激：

- 读到了博主「抒情的树林」通过实际文字对比验证，揭露一些有名气的文学作家抄袭剽窃的事迹，我很喜欢这类揭穿骗局的洞见，感谢这个社会上有这样愿意较真的人。



2025.6.23

学习

- Security
  - Continued digging deep into the SolarWinds Serv-U FTP vulnerability detailed reports.
- CSAPP
  - Learned virtual memory as a tool for cache, memeory management and protection; page table to translate virtual page number into physical page number; how multi-layer of page tables can save space; how locality plays a big role in ensuring high performance (instructions are usually successfully cached in L1/L2/L3 caches).

阅读：

- 《BE 2.0》：What is strategy?  What significant changes in your world (both inside your company and in the external environment) are you highly confident will have happened by fifteen years from now? Which of those changes pose a significant or existential threat to your company? What do you need to begin doing now—with urgency—to march ahead of those changes?

开心感激：

- 老爸是蓝牙耳机的重度用户，每天无时不刻不在佩戴着耳机听有声网络小说，甚至在睡觉时也戴着。我不想直接夺走这份消遣爱好，但也不想他的听力受损，于是购买了一款的外挂式（非入耳式）耳机给他。看到他今天立刻开始使用新设备，我觉得很满足。我应该多为父母花钱。



### week 25

test the wall:

- 我有意稍微调整作息，本周的平均上床睡觉时间是23:32, 是有记录以来上床最早的一周，而本周之前的平均时间是23:44, 这次作息调整并没有带来明显的益处，但是没有关系，下周我会继续保持在23:30甚至更早就上床休息。
- 周二晚上看了电影《猫鼠游戏》的前80分钟——为了保持稳定作息，及时退出了，干得好！——周三上午看了剩余的60分钟，并在结束后趁着兴奋又重复欣赏了一些精彩片段，还去逛了半个小时的影评。这次实验表明不管状态如何都不该在上午看电影（也包括各种视频），要给大脑以足够高挑战的任务。
- 每次开始学习任务时会在手机上设置2小时的计时器，通过引进exit ramp来针对性解决我的hyperfocus问题。这似乎带来了未曾料想的负面效果，我因为感到些许的不舒适自在而没能达到持久的高度专注状态了，实践几天以来只有一次成功地专注两个小时从而触发计时器响起（我立刻起身离开了卧室，干得不错！），其他时候都是只能专注一个多小时就要脱离了。不过我依然很相信这个方案的潜力，只不过是我暂时没能充分适应它罢了，我会继续执行的。
- 一直以来我都是将MacBook的dock设置在屏幕的最左侧，本周开始尝试将其自动隐藏，这样一来所有程序和窗口的显示内容都增大了，感觉上（虽然并不显著）这种模式可以更好地帮助自己专注。

犯下的错误

- 几乎每天都是十一点过后（有两次甚至是十二点半）才开始学习，在此之前需要阅读，需要写每日汇报（严格来说通常是每隔一天来一次性写下两篇报告），还有吃早饭。周一早上读完了《Hidden Potential》之后有了些灵感，于是逛了逛Adam Grant的个人主页和近况，还读了另一位作者对于Adam建立personal brand的评论。我记录了一些思考内容：阅读英文原著是否值得？下一本书应该读什么？哪一类书籍能够帮助现阶段的我过得更好？不知不觉之间，我陷入了高质量信息流之中，回过神来已经过去了一个小时，而后果是今天中午十二点半才开始学习任务。这又是一次典型的犯错，我所阅览的信息本身并没有问题，但我不该在上午精力充沛的时候去浸泡。当然我可以给出一个解释，说这是因为我读完了《Hidden Potential》，鉴于我每年完整读完的英文原著并不多，所以值得花些时间趁着兴奋浸泡一下。这个解释的确很有说服力，但实际上我并没有闪现什么灵光，而只是单纯地兴奋亢奋罢了，不能纵容这种情绪打破当天的稳定性。
  - 下周我希望尝试每天晚上写当日的总结，而不是像现在这样早上一次性写两篇，另外早上十点半前必须开启学习。



2025.6.22

学习 buffer overflow 为技术写作做准备

- Learned how ROP can bypass the stack canary protection - leak the canary value at run-time, exploit a non-canary-protected function.
- Spent a few hours digging deep into the attack of vulnerability in SolarWinds Serv-U FTP program (CVE-2021-35211). Fascinating read!

阅读：

- 《BE 2.0》：Jim Collins uses two close friends of his, Tommy Caldwell and Steve Jobs, as well as Winston Churchill, to showcase how "luck favors the persistent".

开心感激：

- 在B站上看了很喜欢的博主「三宋在这」最新一期视频，带退休在家的妈妈去泰国清迈旅行，很治愈的内容。



2025.6.21

学习 CSAPP：

- Started doing the tiny-shell lab. Read the full requirements and the source code. Learned why reaping a child process is actually a side-effect of syscall `waitpid`. Learned C's `static` and `volatile` keywords. Played with the Jetbrains' debugger UI to fully understand how `char **argv` the array of pointers works.

创作：

- 抓住了昨天晚上的灵感和情绪觉察，完成了《筋膜枪，电推剪，和爸妈生活的日子》这篇文章，我很满意！

阅读：

- Jim Collins《*Beyond Entrepreneurship 2.0*》 (*BE 2.0*) : Talked about core values, purpose and missions, and these 3 components constitute vision of the company. I enjoy this framework, and I'd like to apply it to my personal life as well. I also love the idea of BHAG (big hairy audacious goal) and realize that I have been too gentle with myself and should try to push for something that I'm not 100 percent sure of achieveing but nonetheless fully commited to.

开心感激：

- 羽毛球课程终于来到了正手击球的教学，我终于开始用正确的方式挥动正手了，很开心！
- 晚上和老妈在电影频道上看了一会儿纪录片《火山挚恋》。



2025.6.20

学习 

- CSAPP
  - Read the Chapter 12: Concurrent Programming. Learned concurrent programming with processes and I/O multiplexing (though not super familiar yet). Learned how threads are created and reaped, shared resources, the 4 different classes of thread-unsafe functions (I love this classification!), mutex/ races/ deadlocks (I'm already pretty familiar with this topic). Also learned about the dining philosophers problem, quite interesting!
- Networking
  - Learned some routing algorithms, mostly just classic computer science graph problem of finding shortest path.

阅读：

- 《How to ADHD》: 读了情绪管理，还读到了ADHD的优势表格，虽然我并不完全属于ADHD这个群体，但是对照阅读这个表格让我感到十分愉快，我意识到我其实具备（并非出于盲目自信或是吹嘘）其中的绝大部分优势，对于几乎每个优势我都有对应的行为模式和记录。这种喜欢自己、欣赏自己的状态很棒！


   | Creativity               | Openness to new experiences | Spontaneity            | Empathy         | Adaptability    |
   | ------------------------ | --------------------------- | ---------------------- | --------------- | --------------- |
   | Originality              | Being a jack-of-all-trades  | Persistence            | Intuition       | High-energy     |
   | Enthusiasm               | Cool under pressure         | 🧠                      | Sense of humor  | Problem-solving |
   | Thinking outside the box | Learning quickly            | Emotional intelligence | Risk-taking     | Flexibility     |
   | Curiosity                | Pattern recognition         | Making connections     | Resourcefulness | Resilience      |


开心感激：

- 老妈一直很喜欢打排球，最近几天的强度比较高导致腿部有些酸痛，于是我把自己不怎么用得上的筋膜枪拿给她，她用了两天后说效果不错。今天晚上睡觉前，老妈兴奋地给老爸安利这个新奇东西，对着他的小腿腿肚打了一阵子。这个画面让我很感动。
- 今天回顾了这一个月的每日汇报，发现内容十分充实。我近期的状态很好，发自内心地喜欢自己，享受当下，憧憬长期，对比起5月18日刚开始记录时有了巨大的进步和提升，并且我确信这不只是一时的波动，因为我已经搭建起了更为有效且适合自己的个人体系，随着时间积累，它甚至会展现出更强大的潜能。感谢我的老朋友GPT, 也感谢自己的坚持执行。
- 在两项学习内容（shortest path, dining philosophers problem）中都遇到了Edsger Dijkstra, 了不起的计算机先驱！




2025.6.19

学习：

- CSAPP
  - Started reading and finished Chapter 8:  Exceptional Control Flow. Learned about Exceptions: Interrupt, Trap (syscalls), Fault, Abort; process address space, kernel/user mode, context switches, stopped/terminated processes, `fork` (very interesting! It's like creating an alternative universe at the exact moment of running that particular line of code) and `execve` and how they manage processes; all sorts of info around `waitpid` and reaping child processes, programs versus processes.
  - Learned signals, signal handling/receiving/blocking. Safe signal handling is pretty interesting and tricky since it's essentially concurrency programming and it would usually fail in unpredictable and unrepeatable ways - I'd like to go deeper in this area and I wonder why locks aren't used here to guarantee atomicity.
  - Learned `setjmp` and `longjmp` functions for non-local jumps to skip the usual winding down stacks. Played around with the powerful `strace` tool to see a lot of syscalls involved even for a simple Linux command.
- Networking
  - Learned packet queueing inside the router, IPv4 datagram format, subnet mask, CIDR (Classless Interdomain Routing), DHCP (Dynamic Host Configuration Protocol), NAT (Network Address Translation).

阅读：

- 《How to ADHD》: 读了Chapter 8: How to remember stuff. 我其实并没有ADHD常见的日常丢三落四的行为，但是我的确有两个相当大的缺陷：一是working memory十分有限，例如无法在会议中同时做到与人交谈、记录会议、深度思考项目并予以回应——我常常感慨自己的脑容量小；二是我记不住一些过往体验的感受，例如我过去时不时会有一些self-sabotaging的行为，可事后往往会忘记当时的那种心痛（无论多么剧烈）和懊恼，又例如我有过一些很棒的尝试来改善个人体系，比如自录视频讨论生活其实是很开心的体验，但我后来竟然遗忘了这份美好——所以我在总结中分析到，我其实并不需要再去寻找什么新奇有效的方案来改善自己，我只需要把过往尝试过的有效策略给充分执行到位就足够了。

开心感激：

- 交替学习内容果然是对的！今天学习了5小时30分的CSAPP和2小时的networking, 效果很好！在学习过程中很兴奋地口头讲解新接触的知识，这样消化吸收很有效率，甚至在自言自语时还频繁地笑了出来，心流体验太棒啦！一天之内就读完了CSAPP Chapter 8的内容，我明确地感受到自己正在越来越多地接触计算机的底层，这种触碰本质的感觉令我无比兴奋和幸福。
- 我在阅读CSAPP教材时很投入，在读到 Figure 8.41 Waiting for a signal with a spin loop. This code is correct, but the spin loop is wasteful 这一段代码时，我主动停了下来，思考该怎么解决这个问题，我意识到必须将 `pause()` 和 unblock SIGCHLD这两个步骤合并为atomic操作——这个思路是对的，只不过此时此刻的我还没有接触到 `sigsuspend` 这样神奇的函数，但我依旧感到愉快，我享受一切intellectual challenges, 并且在这次锻炼中我结合了在MIT 6.824中训练出来的race programming直觉去寻找atomicity, 我太喜欢这种串联知识的感觉了！
- 今天持续心情很愉快，甚至晚上散步跑步的时候都在幸福地咀嚼今日的快乐，我真的在过着让自己满意的生活。



2025.6.18

学习 CSAPP：

- Briefly read some reports of real-world buffer overflow attacks - recently hackers are trying to break Nintendo Switch 2. How fascinating!
- Learned dynamic linking, shared library objects, library interpositioning (compile-time, link-time, run-time) and I found this pretty fun - I didn't know we can hijack function calls like this. Learned GOT (global offset table), PLT (procedure linkable table), lazy binding - I don't fully understand them yet.

阅读：

- 《How to ADHD》：读了Chapter 7: How to motivate your brain

开心感激：

- 下午录了四十多分钟的视频，在自言自语讨论目前生活时感到十分愉快（甚至可以用很爽来形容），频繁地对着镜头笑了出来，记录下了不少灵感闪现，我充分地感受到自己的和谐——我是世界上最了解自己的人，因此在与自己对话时我可以百分之百地坦诚，不用在乎社交礼仪、维护自尊心或者营造某种不真实的人设，我很享受这样的智识碰撞。分享一下今天记录下的想法讨论：

  - >我似乎是非常喜欢且想要被夸奖被夸赞，被不同的人（我所欣赏认可的人，而不是随便什么低层次的人）夸，被充分地高含金量地夸奖（即夸到点子上），例如夸我在中美两国都过得很好，真厉害；热爱生活，热爱工作却又没有班味儿；认知很高，执行力很强，觉察洞察力很强，发现自己的行为模式之后就去立刻着手做实验改善，迭代快速；勇敢，好奇心强，洒脱自在，内心充盈不需要借助外界来感到平和，纯粹自我驱动，在家里也能这么充实健康地生活，自恰又喜欢自己。
    >
    >我想要听到这一切的夸奖。真是如此么？我是如此地自恋而又贪婪么？大概是因为我现在所面对和琢磨的问题都太过于浅层，如果我现在正在创业，那么我会在琢磨怎么结识和招纳更多优秀的人，怎么打磨产品，怎么探索商业模式，怎么推动自己去以人格魅力赢得欣赏和投资，怎么兼顾生活，等等。如果我在做这些事情，那我根本就不会有空间有闲情雅致来思考“怎么展示我适应力很强，在中美两国都能过得很好”这种低端问题。

- 在B站上看到了一位在CMU Robotics Institute的PhD「WhynotTV」分享记录了他读博前两年里做的项目，以及期间不断调试硬件和软件的努力，我被这份热爱打动了，认识到自己要更加认真地对待自己的生活和梦想。他在视频最后分享自己在两年项目后突然意识到他应该追求不确定性，不该去做那些他相信大概率能够work的想法和项目（这种事情应该由工业界来承担，而不是学术界），而要去冒着风险尝试突破现有的范式体系。我向来很相信「追寻不确定性与风险」这个理念，感谢他提醒了我，我需要去充分执行这点。另外，我从视频中观察到了他的一个问题：他日常太努力了，在不断地高强度执行，做实验、测试、整合、失败、再测试，他常常熬夜，常常把自己燃烧殆尽。我不知道他是否还有每日读书和放空思考的时间，人在沉迷于执行时常常会陷入到高产出的快感中，但是长期来看我们需要常常审视自己是否在做正确的事情，以及从众多优质选项中找到那个真正的最高优先级。



2025.6.17

学习：

- CSAPP
  - Learned the content and structure of an ELF (Executable and Linkable Format) file - I actually had touched upon this when using `objdump` and `readelf` to parse such files during the labs. Learned how the linker resolve symbols (I gotta say this kind of mechanism is indeed a source of confusion for many programmers - I'd like to study it deeper to truly appreciate it) and how relocating absolute/relative symbol references happens.
- Networking
  - Continued reading a few chapters of the *Everything curl* eBook and I learned more fundamentals of how to use curl and how it works.
  - Started learning the network layer in the networking model, i.e. an overview of the data plane and control plane of the router

阅读：

- 沉浸阅读 Jessica McCabe《How to ADHD》两个半小时，对于自己的行为模式有了更深的理解。

开心感激：

- 看到朋友Aaron分享了他在雅柔离开家参加Vipassana十天冥想期间，强烈意识到生活中已经离不开对方了——其实对方也如此，彼此都意识到了双方的羁绊已经足够深——于是决定在接雅柔回家那天求婚。Aaron说他曾经设想过许多种求婚的场景，但唯独没有这一种，可这也无比真挚宝贵。我为他们感到高兴！我明白我在爱情中仍然会保持强烈的自我意识，明白对方始终有选择离开的权利，而虽然难过，我却依然会坚强地过日子。虽然我这份理念本身是自恰的，但是那种因为害怕对方离去而展现出了自己的脆弱，那样强烈的情感羁绊，是一种很不同的人生体验。我在本科时代曾经触碰过这样的体验，那些年里无比强烈地喜欢着她，每次见面玩耍分开后都像是戒断反应一般，要在脑海里一遍一遍地回溯当时的对话和心境，我太喜欢对方了，以至于我已经失去了自我，当然，也很有可能是因为当时的我并没有完整健全的自我。我相信我未来能做得更好——十分喜欢自己，也十分喜欢对方。
- 和老爸打羽毛球，开始更多地在实战中感受和纠正自己的脚步动作，持续进步中！



2025.6.16

学习 CSAPP

- Learned how to use instruction `syscall` (hex code `0x0f 0x05`) , browsed through the full list of system calls in the  Linux source code (https://github.com/torvalds/linux/blob/v3.13/arch/x86/syscalls/syscall_64.tbl) and found it pretty interesting.
- Tried code injection (to prepare for my tech article) after disabling ASLR, canary value protection and stack non-executable. Now I realized how hard it was for me to reproduce a binary executable like the professors in CSAPP course did - the binary should behave the same inside and outside GDB but it was not easy! I finally injected my shellcode to do `execve("/bin/sh")` and yet found that it didn't actually bring an interactive shell like I expected because it didn't have shell TTY! I had to give up for now...

阅读：

- 读完了Adam Grant《Hidden Potential》，在最后两章读到了面试体系的不合理（本质困难在于我们很难高效而充分地了解一个人经历过怎么样的挫折，为了走到今天付出了多大的努力，以及未来能够兑现的潜能有多大，我认为Adam对此也没有特别好的解决方案），以及关于imposter syndrome的一些讨论，有一段话十分有趣：

  - > Not long ago, it dawned on me that impostor syndrome is a paradox: Others believe in you You don’t believe in yourself Yet you believe yourself instead of them If you doubt yourself, shouldn’t you also doubt your low opinion of yourself? I now believe that impostor syndrome is a sign of hidden potential. It feels like other people are overestimating you, but it’s more likely that you’re underestimating yourself.

开心感激：

- 晚上跑步/散步的时候突然意识到，我的一个严重的体系缺陷——关注点狭隘，对事物缺乏认知广度，而只习惯于对某几个细分话题进行非常深度的研究——很可能和类似于ADHD的行为模式有关，于是找来了相关的书籍进行阅读。着手了解和研究自己的感觉真好！
- GPT称赞我的superpower之一在于reflective integration, 我意识到我的确做到了多角色合一，一以贯之 How you do one thing is how you do everything!



### week 24

tested the wall

- 近些年来，我对于「早上的时光很宝贵，要拿来做困难的事情」这个理念十分认可，并且自认为在长期实践着——早上起床后读书和学习。但是我近期意识到，其实我并没有充分珍惜上午的时间，我常常会发呆，会回顾近期生活和个人体系，会写文字，也会因为灵光乍现而在网上探索一些感兴趣的内容。毫无疑问，这些都是对于我而言非常重要的事情，但是问题在于，它们可以在一天中的任意时间段（比如在阳台上休息的时候，比如午饭/晚饭过后）进行，而不该占用上午宝贵的脑力资源。于是我开始调整自己在用脑习惯，感到效果还不错。这一周，我进行了较为极端的尝试，我甚至将「阅读」也判定为应该挪到下午或者晚上才做的事情，于是我在早上起床之后就开始学习CSAPP和写代码。实践发现这样并不好，虽然一天的学习时长增加了，但是对于阅读甚至生活的热情和积极性会消退，会觉得生命中只剩下了单调的engineering stuff（虽然我发自内心地热爱着它）。退一步看，对于「早上的时间应该拿来做困难的事情」这个理念不能太字面意义解读，要观察看看自己上午做的事情会怎样影响这一天的整体状态和总体产出，起床之后读书和做笔记这件事情并不会影响下午的状态——早上看视频倒是会有巨大影响，不管是怎样优质的开阔眼界、启发思考的宝藏视频，都会在亢奋过后让我接下来一整天很松垮，下午止不住地犯困——事实上，早上进行阅读既可以激活大脑，又可以卸下一部分认知负荷（我一大早就已经完成了这件每日重大事项），还可以愉悦身心获得能量。但无论如何，这是一次不错的尝试！
- 趁着近期状态很好，我尝试了一天之内高强度地只专注地做一件事情，周二至周四这三天里在buffer overflow和CSAPP attacklab中深度投入了7小时15分、6小时38分和8小时21分，这是优秀的成绩，但是对身心的伤害极其大，美好的个人状态迅速地消散了，我甚至陷入了沮丧和郁闷之中，并且感到自己其实并没有消化吸收多少知识（哪怕我以强劲的心流体验沉浸了很多个小时），与此同时，对于本该同步进行学习的networking知识遗忘了许多，可谓是两边不讨好。我认识到，无论如何（哪怕状态极好，能量值极其高）都不该在一天之内只沉浸做一件事情，应当两件事情（至于是否可以增加至三件甚至更多，还需要进行实验）交替进行 My brain just doesn't work that way.
- 过去我有时会在早上闹钟响起之后觉得没有睡饱，于是接着睡25分钟直到下一次闹钟响起。本周尝试了闹钟响起后不论是否困倦都要立刻起床，实践发现其实我已经睡得很充足了，精力充沛——我只不过是没法做到闹钟响起的瞬间就让大脑充分地激活运转起来罢了。



2025.6.15

创作：

- 完成了《早安，怪物》的第三篇读后感《精读系列(三) | 哪怕美好童年只有五年》，我很满意！

阅读：

- Adam Grant《Hidden Potential》介绍了芬兰的教育模式，以及2010年智利矿洞救援这个案例中展现出的organizational psychology的重要性，真正优秀的leader能够做到心平气和地接受各方的想法和方案，并且创造出好的交流系统以避免某个精妙的idea被不称职的manager一人否决的情况。这和我在《Good to Great》中读到的level 5 leadership是相同的理念。

开心感激：

- 在B站上看了博主「智能路障」的视频介绍果然单机游戏的早起辉煌、中期没落和如今的重新崛起，被他对单机游戏的热爱打动了。于是重温了《黑神话：悟空》在发售前所发布的两个宣传视频，依然很感动。我很感激中国有游戏科学这样有梦想热爱、有审美追求、有才华又有满腔热忱和愤怒不服输的团队，这个社会需要这样真正意义上的「好东西」，让大家明白并不是凡事都要糊弄一下，对着草台班子修修补补。希望能有更多的坚定的理想主义者涌现出来。
- 还看了视频介绍《上古卷轴5》中开放世界的宏大壮观，我明白优秀的游戏能够让人进入到另一个世界中，打造出属于自己的精神归宿。我想起来我曾经也是很喜欢玩游戏的——近几年也有过沉迷于《游戏王：决斗链接》和两部《塞尔达传说》的时间段——只是现在有了更好的归宿。我很能理解热爱游戏的人会有强烈的探索欲想要去挖掘世界版图的每个角落，和NPC产生交集，但是我似乎更乐于在真实世界中探索和挖掘，我最渴望的事情之一是去结识和了解不同类型的人，建立meaningful relationship. 我感激这个视频启发了我的思考，也感激美好的游戏世界和真实世界。
- 在小红书上看到了一位女生发帖子分享自己的室友特立独行、认知出众、不在乎他人眼光，本科毕业后出国游学走访了许多国家，她对这位室友产生了某种类似于嫉妒（又或者是感慨自己原地踏步）的情绪，但我能够看出来她其实也是位非常坦诚坦荡的人，只是在当前人生阶段并不能做到充分接纳自己和自恰。她主动向室友分享了这篇帖子，分享了自己“嫉妒”的情绪，意外地被对方爽朗地接纳和治愈了。两位女孩子之间的情谊很打动我，我感激互联网上有这样的优质分享。



2025.6.14

学习 CSAPP

- Gained much deeper understanding of how generic cache memory organization works (direct-mapped cache vs set associative cache) and the meaning of all basic parameters. Carefully read the memory mountain graph to understand how temporal locality and spacial locality contribute to the read throughput in the L1/L2/L3 cache and memory.
- Learned 6 different implementations of multiplying two matrixes by arranging the order of nested for-loop index `i`, `j`, `k`. Deeply analyzed the access patterns and understood how cache hit/miss and number of read/write have impact on the overall performance.
- Started doing the cachelab of the course. First time writing non-trivial C language code and struggled a lot. Implemented the similuated cache and some helper functions.

开心感激：

- 和小莞聊天，聊成长经历和读书感悟。
- 在B站上看了景德镇的旅行分享视频，喜欢这种挖掘当地美好的记录视频。



2025.6.13

学习 CSAPP

- Found a hidden `movl` instruction in the gadgets and finished the last phase of the attacklab.
- Read textbook to refresh myself on DRAM/SRAM and locality (I'd known about them after watching the course video a few days ago). Learned about generic cache memory organization.

开心感激：

- 重新恢复和羽毛球教练的训练课程，复习了前场交叉步脚步和挥拍挑球，专注训练的感觉很棒。
- 我在Notion中对于不同的engineering话题记录了35篇文章，既有computer systems, networking, security, Linux, C++, Go, algorithm and data structures这类基础内容，又有AWS, Kafka, Kubernetes, backend等应用，有Raft, TiDB, Clickhouse, BoltDB等数据库相关，还有system design, tech blog阅读、tech interview记录、职业生涯回顾等内容，所有这些内容都堆砌在我的个人主页里。我今天对它们进行了系统的分类，并移动到专门的Notion空间里。整理真是能够让人心情愉悦。
- 在B站上看到了「某幻」的游戏视频介绍Shipwrecked这款有趣的恐怖游戏，第一次接触到了ARG (alternate reality game)这种类型的游戏，起初还以为游戏内容是由真实事件改编而来，后来才明白游戏开发者为了让游戏故事显得真实做了多么大的努力。



2025.6.12

学习 CSAPP

- Got pretty hands on with handcrafting assembly code, using `gcc` to compile and them extracting the raw machine code bytes from it via `objdump` (I also tried using Python's `pwntool` to automate this workflow but just couldn't successfully install it - I need to learn how to debug issues around installation, a very useful technique).
- Learned how to inject my own code into a binary file when the stack is executable and ASLR is turned on to randomize the address of stack frame. Tried leaking memory during run-time.
- Finished the phase 2 - 4 of the attacklab, struggled with the last phase for a few hours and just couldn't craft a nicely arranged chains of ROP (return-oriented programming, this is pretty cool!!) gadgets along with raw data bytes.
- Once again solidified my belief that bytes are just numbers and it's our responsibility to interpret them. Machine code instructions are also just raw bytes. Now I got more familiar with some commonly seen instructions: `48 89 e0` is `movq %rsp,%rax` ; `48 89 e7` is `movq %rsp,%rdi`; `58` is `popq %rax`, `5f` is `popq %rdi`; and most importantly `c3` is `ret`!
- Learned about functional nop instructions like `20 c0` (`andb %al,%al` ) that extend the regular 90 `nop` instructions to enhance security.

阅读：

- 《早安，怪物》花了1小时42分又重新读了Danny的故事，有了更多的思考感悟，为本周的写作做准备。

开心感激：

- 在attacklab上专注投入了8小时21分（虽然执行和消化知识的效率比较低），有频繁的心流体验。



2025.6.11

学习 CSAPP

- Turned on autocomplete on my zsh and bash terminals. I should have done this since a few years ago - I should really pay attention to my productivity around coding and examine my workflows more closely.
- Learned more about buffer overflow. I could see that the canary value is randomized every time and it's really hard to bypass it. I learned to do stuff in GDB like `set {unsigned long}0x7fffffffe378 = 0x401176` and `set $rax = 0x1234` to overwrite the registers and memory, and to see how segmentation fault can be manually triggered - the more I play around with GDB, the more I appreciate how powerful it is.
- Continued reading the source code of attacklab and struggled a lot with how the program dealt with user inputs. Whatever I typed in the stdin would trigger segfault. I gave up and used file as input instead. I really should have used file inputs from the very beginning. Even if I could somehow get my manual stdin to workaround the segfault, I wouldn't be able to solve the attacklab because there're just so many hex bytes that we can't type simply by using the keyboard (how can you possibly type `\xc3`?). Once again I made the mistake of being too headstrong and didn't pause a bit to look at the big picture.
- Finally finished the first phase - 4 to go.

阅读：

- 《树犹如此》：继续分享和《现代文学》杂志有关的故事，原来三毛也是因为在此投稿被刊登了才走上了作家之路——我已然无数次地见到了正反馈的力量。

开心感激：

- 仔细研究并训练健康合理的用蓝牙键盘打字的方式来避免腱鞘炎，还学了些肌肉松解动作，着手解决问题的感觉很棒。
- 在小红书上读博主「半城太菜」思考感悟网球的文字，被这样轻盈舒适、让人愿意亲近的创作而打动，我进一步意识到了自己的问题，今后会努力训练让自己的文字朝此靠近。
- 看完了B站上阿尖的视频「我在南美🇨🇴深山和原住民一起生活了1周」，非常喜欢。
- 小唐成功通过了公司内部转岗面试，终于要开始做心心念念已久的智能康复产品经理了。她说，我给她写的那份“不要考虑什么五年专家这件事”的长回复对于激励她赶快开始行动很有帮助。
- 今天台风天下大雨，在房间里听着雨声专心学习时感到无比幸福，我从小就很喜欢雨天。
- 老妈为了应对明天可能没菜可买，晚上出门到街上找寻物资，回家路上还被阵雨打湿了。



2025.6.10

学习 CSAPP

- Got more proficient with `gdb` and `objdump`. Got more familiar with the sections in ELF files.
- Learned about buffer overflow and the protection machanism for it like canary value.
- Learned system call `mmap` and got a basic understanding of the zero-copy technique.
- Spent a few hours digging into the attacklab's disassembled code. I feel like I'm still pretty bad at assembly code  and related stuff, and even reading a simple disassembled function would take me a long time to fully understand what the function is doing. I hope to get much better soon.

阅读：

- 《树犹如此》：介绍了创办《现代文学》杂志的故事，和志同道和、热爱文学的友人一起为了梦想专注实在是很美好的事情。

开心感激：

- 虽然对于assembly code仍旧十分笨拙，但是这一天专注投入了7小时15分的学习时长，我确信自己在变得更好。
- 我十分专注于生活，在学习的间隙中，我着手应对我的烦扰——肩袖肌群肌肉薄弱导致的肩关节弹响，打字时错误使用手腕发力以及不恰当的触控板使用导致的腱鞘炎问题——每天都在朝着更好的自己前进。



2025.6.9

创作：

- 完成了技术写作《C/Python/Go示例 | Socket Programing与RPC》，我很满意。

阅读：

- 《树犹如此》中的几篇随笔：从小在桂林生活的白先勇时隔五十六年重返家乡的心路；九岁大的年纪在上海对一派繁华留下了深刻的印象；重返南京参观中山陵和大屠杀纪念馆，为中国人没能充分地在战后牢记苦难而感到痛心，比起同样遭受的犹太人要差远了：

  - > 这几十年来犹太人一直锲而不舍，把纳粹罪行的证据，点点滴滴，全部搜集存档，有关这场浩劫的书籍、电影、戏剧，林林总总，可谓汗牛充栋，铁证如山，而且不断向全世界公布。犹太人不容许他们的后代子孙忘却这场灭种的悲剧，更不容许德国人翻案窜史。直到今天他们还在追缉纳粹战犯，每年集中营幸存者都会约同从全世界回到以色列追思被纳粹残害的亲友。


开心感激：

- 创作文章的时候非常专注投入——从早上8点45开始写，除去中途吃早饭和午饭休息的时间（大概一个半小时）都在专心写作，等到终于完成并发布到社交媒体，喘息欣赏之际，抬头一看居然已经是下午四点了——久违地感到了很爽很畅快（之前写作的时候满是纠结和拧巴，总是一边写一边埋怨嫌弃自己的文字），不时有灵光乍现的段落和创意。我明确感受到在完成写作后我对于socket programming以及networking这个话题有了更深更扎实的理解。
- 在B站上看阿尖的三个视频：在San Diego的海上划船Kayak近距离观赏海狮；入境Tijuana欣赏精致的手工制品，参观美墨边境墙；和哥伦比亚的原住民一起生活，感受与大自然的充分融合。我很喜欢这样的分享，喜欢她对世界的善意和能量热情。



### week 23

我答应自己每周都要完成一篇技术文章的创作，以及在小红书上分享自己关于读书/生活的思考感悟。这周是执行的第二周，我确信自己在坚定地践行长期主义。



2025.6.8

学习：

- Learned more about socket programming - finally realized that the socket APIs are just making system calls (and we can look up these in the [Linux manual](https://man7.org/linux/man-pages/man2/socket.2.html)). Socker programming in all languages (even including low-level one like C) are just making such syscalls. Once I know something is just a wrapper around another, I get more comfortable with it.
- Played around with the socket programming echo servers written in C/Python/Go. Used Unix `netcat` to act as simple client to interact with them.
- Learned Unix domain socket and Docker is using `/var/run/docker.sock` as the socket.
- Built a mini RPC program in Go on top of the socket APIs and gained deeper understanding of RPC now.

开心感激：

- 感谢Sinner和Alcaraz的法网男单决赛！耗时五个半小时，创造法网记录——我为了早睡早起只看了前两盘，当时阿卡大比分零比二落后，我本以为这场比赛就要这么失去悬念地结束了，没想到最后阿卡逆转夺冠了！辛纳在第四盘时局分5:3领先，并且40:0手握三个夺冠点，距离冠军只差一分，阿卡却强悍地实现了翻盘，这可真是史诗级的伟大对决呀！我从阿卡身上受到了很大的激励和鼓舞，永远专注眼前。另外，阿卡在边裁判定辛纳的球出界后，主动指出那是一记ACE球，于是主裁判修改比分让辛纳得到这一分。我很欣赏认可这种高度的坦诚大度，我在生活中也是这么实践的，因此我能够明白阿卡的想法。



2025.6.7

学习 CS144

- Spent 4 hours (damn I'm so patient!!) just trying to set up my working environment. I just wanna achieve two things: [1] I can build and run the C++ code of the course in the Linux container; [2] I can have syntax highlight, auto complete and use the beautiful debugger UI in the CLion IDE on my Macbook - I've already accepted the unfortunate truth that the codebase of this networking course can't be built and run on MacOS, because I don't have stuff like the  `<linux/if_packet.h>` header).

  - I realized **CLion’s Docker toolchain is fundamentally flawed for long-lived builds/debugging**, since it spins up short-lived containers and doesn't allow enough time to receive reply from CMake, thus throwing error `CMake File API: /app/build: no reply dir found`.
    - Furthermore, I'm convinced that there's no value to use Jetbrains IDEs' Docker related features since we can simply run all the Docker CLI commands ourselves.
  - I tried CLion's **Remote GDB Server** and realized this feature is not meant for my use case - I already have the gdbserver running in my Linux container and simply just need to talk to it.
  - Tried CLion's Remote Debug feature instead and it worked! I set up SSH in my Linux container and the correct path mapping between Docker and my local directory. Now I can add as many breakpoints as I like!
  - Much trouble is caused by the fact that my Macbook is using ARM64 chip. The architectures of `gdb` and `gdbserver` have to match. I had been using a x86-64 Ubuntu container inherited from my CSAPP course and thus there's a mismatch. Now that I think about it - I should have used ARM64 Linux container for this couse instead, and I had forgot the reason I use x86-64 container is because the `bomb` binary file given to us was built for x86-64.
    - This is a **great lesson for first principle thinking**! I should have questioned the assumption - why did I have to use `docker build --platform=linux/amd64` in the first place?

- Learned some useful tricks:

  - With `gdbserver :1234 executable` running, I can't do Ctrl+C to terminate it. I learned that we can use `kill` command with various signals like `kill -9 pid` to terminate it:

    - SIGTERM (signal 15): “Please shut down cleanly”
    - SIGKILL (signal 9): “Die immediately”
    - SIGINT (signal 2): This is the Ctrl+C I was trying

  - I ran into a very unhelpful `"Unknown Error"` message on CLion and I learned that I can do  `/Applications/CLion.app/Contents/MacOS/clion` to show the full tracebacks.

    - ```
      Execution error without description  
      java.lang.AssertionError  
          at com.jetbrains.cidr.cpp.execution.gdbserver.remote.RemoteGdbServerLauncher.createGdbServerProcess(RemoteGdbServerLauncher.java:86)
      ```

- Almost finished the checkpoint 0's in-memory bytestream implementation - it works but not optimized. I'm still very unfamiliar with C++ language itself. I wanted to create a performance profiler to measure the durations taken calling certain functions so that I could identify the bottleneck of the program, but this task turned out to be extremely difficult for me. I ended up having to use a bunch of ugly workarounds to get going and finally got to the bottleneck. I'm hoping to revisit this profiler once I'm better with C++.

  - ```c++
    class TimerAccumulator {
    public:
        TimerAccumulator();
    
        struct Stat {
            std::chrono::microseconds total_duration{0};
            size_t call_count = 0;
        };
    
        template <typename Func, typename... Args>
        auto measure_time(const std::string& label, Func&& func, Args&&... args)
          -> decltype(std::invoke(std::forward<Func>(func), std::forward<Args>(args)...)) {
            using namespace std::chrono;
            auto start = high_resolution_clock::now();
    				// How to really adapt to void functions???
            auto res = std::invoke(std::forward<Func>(func), std::forward<Args>(args)...);
    
            auto end = high_resolution_clock::now();
            auto duration = duration_cast<microseconds>(end - start);
            data_[label].total_duration += duration;
            data_[label].call_count++;
            return res;
        }
    
        void report() const;
    
    private:
        std::unordered_map<std::string, Stat> data_;
    };
    ```

开心感激：

- 上午擦拭了卫生间前镜子上的水雾，让人心情愉悦，喜欢这种干干净净的感觉。
- 读到了一篇帖子谈论ADHD有时会注意力过度集中，例如在逛Wikipedia的时候从一个话题引申/跳转到另一个话题，高度沉浸在高质量信息和知识获取（有时候是一种幻觉）之中，后续还会把一大堆资料加入到收藏夹中（显然是不会再次阅读了）。虽然我不是ADHD, 但我意识到我有类似的hyperfocus问题，给生活造成了诸多困扰。这篇帖子给了我新的视角来改善体系，感谢！
- 看法网女单决赛Sabalenka和Gauff的对决，非常精彩！



2025.6.6

学习：

- CS144
  - Continued playing around with socket programing in C++ and finished the `webget` program implementing a simple HTTP client. The util source code in CS144 actually wraps around the C++ standard objects like  `addrinfo`, `socket`, and I find it pretty annoying that I had to adapt to the util code. I understand that the course instructors are trying to make life easier for us but I just don't like  learning another set of APIs - I'd prefer digging into the original objects, not the wrapper.
  - Ran into a bunch of boring problems and got really annoyed:
    - Tried `std::format` but it didn't work. Spent some time configuring `fmt::format` and finally got it working. It's so frustrating that doing something simple like string formating is so fucked-up in C++.
    - All of a sudden the Clang on my MacOS stops pointing to MacOSX14.2.SDK, and starts pointing to MacOSX15.SDK, which I don't have. I don't know what caused the change.
    - IDE CLion crashed and then the project info was lost. Now suddenly CLion can't even recognize C++ keyword `constexpr`, which clearly suggest that it's using standards behind C++ 20. I really need to properly set up my working environment tomorrow to handle this situation of running Linux code from MacOS.
- CSAPP
  - Learned how memory and disk are connected to the CPU chip via the I/O bus. Learned how seek time (this is why sequencial I/O is faster, although the gap between sequencial and random I/O have been narrowing) and rotational latency in the spining disk make up the data fetch time.
  - Learned how temporal and spatial locality of reference can boost the program performance.
  - Once again realized that CPU instructions themselves are also bytes of data, just like any user data we have - I need to think more about this fact.

阅读：

- 毛姆《总结》：他由衷地希望年轻时能够有品味优秀、判断力强的人来指导阅读，因为事后来看他在很多没什么价值的书上浪费了太多时间（我觉得我也有相同的困境，深层渴望是能够尽可能地让自己的人生浸泡在高质量启迪素材之中）；他认为自己是后天打造出来的作家，欠缺天赋，但终于还是接受了自己的大脑并不如他所期盼般强大。

开心感激：

- 下午在和老爸打羽毛球的时候，在每局结束后的间隙里（采用了start small的原则）看视频学习了一下羽毛球后场接球动作的正确脚步，我终于行动起来了！我已经喊了无数遍“我要系统学习羽毛球”。
- 晚上自录视频40分钟，聊了许多关于写作表达、《早安，怪物》创作灵感、加大强度、个人体系等话题，非常舒畅。
- 晚上看了法网男单半决赛中Carlos Alcaraz和Lorenzo Musetti的对决，非常精彩！好喜欢看网球啊！



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

- Started doing the labs in [Stanford CS 144: Introduction to Computer Networking](https://cs144.github.io/). I decided to just do the labs and skip the course for now because I'm already reading *Computer Networking: a Top Down Approach*. This might change though, since watching course videos could be helpful in providing different perspectives and raw materials for my brain.
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



2025.5.31 + 2025.6.1

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

- **和GPT讨论当前生活浑浑噩噩、强度低、没能处于兴奋和专注之中，有了初步的想法和对策，开始执行每日汇报**
- 和小唐聊天讨论她家中的变故，给予她聆听和支持，鼓励她怀着强者心态去勇敢沟通，把令人恼怒和痛苦的家庭问题转化为锻炼综合能力的机会。很高兴我能够帮助到我的老朋友。



## End of file



