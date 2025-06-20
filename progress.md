## 2025年6月

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

- **和GPT讨论当前生活浑浑噩噩、强度低、没能处于兴奋和专注之中，有了初步的想法和对策，开始执行每日汇报**
- 和小唐聊天讨论她家中的变故，给予她聆听和支持，鼓励她怀着强者心态去勇敢沟通，把令人恼怒和痛苦的家庭问题转化为锻炼综合能力的机会。很高兴我能够帮助到我的老朋友。



## End of file

