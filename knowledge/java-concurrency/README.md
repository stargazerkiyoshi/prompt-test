# Java 并发编程学习入口

这是一套按 SLS 组织的 Java 并发编程系统学习内容，面向“已经会写 Java，但并发知识零散”的读者设计。它不是 API 速查，也不是面试题堆砌，而是一条完整学习路径：先把并发问题现场看清，再进入 Java 内存模型、锁、线程池、并发容器与协调原语，最后回收到设计、性能和排障。

如果你是第一次进入这套内容，建议不要直接随机点开某个 JUC 类，而是先从总纲开始，再按章节顺序推进。这样你能始终知道自己当前处在整条主线的哪个位置，也知道某个工具为什么在这里出现。

## 先把“Java 并发编程”这件事的层级位置说清楚

这套内容里，“并发”会在四个层级上出现，但它们不是同一件东西。

1. `并发问题层`：多个线程为什么会让程序结果失控，核心是原子性、可见性、有序性。
2. `内存语义层`：Java 内存模型怎样约束线程之间看见什么、什么时候看见。
3. `同步与协作层`：锁、原子类、阻塞队列、协调原语怎样让线程安全协作。
4. `工程系统层`：线程池、异步任务编排、容器选择、调优与排障怎样影响真实服务。

对应到课程顺序就是：

- 第 1 章讲第 1 层：并发为什么会打破单线程直觉。
- 第 2、3 章讲第 2 到第 3 层：JMM、`volatile`、锁和同步。
- 第 4、5、6 章讲第 3 到第 4 层：线程池、并发容器、CAS 与协调原语。
- 第 7 章讲第 4 层：设计、性能与诊断。

把这层定位先立住，后面就不容易把“线程”“锁”“线程池”“并发容器”混成一团。

## 推荐阅读顺序

1. [00-outline.md](00-outline.md)
2. [第 1 章](chapters/ch01-why-concurrency-is-hard-and-where-java-steps-in)
3. [第 2 章](chapters/ch02-java-memory-model-and-volatile)
4. [第 3 章](chapters/ch03-locking-synchronization-and-happens-before)
5. [第 4 章](chapters/ch04-thread-pools-futures-and-task-orchestration)
6. [第 5 章](chapters/ch05-concurrent-collections-and-producer-consumer)
7. [第 6 章](chapters/ch06-atomic-cas-and-coordination-primitives)
8. [第 7 章](chapters/ch07-concurrency-design-performance-and-diagnostics)

## 三层阅读路线

如果你想最快进入，可以按下面三种方式选路：

- `完整学习`：从 [00-outline.md](00-outline.md) 开始，按 1 到 7 章顺序读。
- `问题导向`：先读 [第 1 章](chapters/ch01-why-concurrency-is-hard-and-where-java-steps-in) 和 [第 2 章](chapters/ch02-java-memory-model-and-volatile)。适合“代码写过，但总分不清竞态、可见性、重排序”的读者。
- `工程导向`：先读 [第 3 章](chapters/ch03-locking-synchronization-and-happens-before)、[第 4 章](chapters/ch04-thread-pools-futures-and-task-orchestration) 和 [第 7 章](chapters/ch07-concurrency-design-performance-and-diagnostics)。适合已经知道一些 JUC 名字，但想把它们放回真实系统设计的读者。

## 课程主线

整套内容围绕一条连续主线展开：

为什么多线程一进场，单线程直觉就会失灵；
为什么“值改了”不等于“别的线程看见了”；
为什么并发正确性不能只靠 if 判断和运气；
为什么锁、`volatile`、CAS、阻塞队列、线程池会同时存在；
为什么真正的工程问题不是“会不会 API”，而是“当前问题该用什么同步与调度模型”；
为什么并发系统最后一定会回到性能、容量和排障。

如果把整套内容压成一句话：

Java 并发编程的核心，是在共享状态、多线程协作和资源边界之间建立受控秩序。

## 贯穿例子

整门课固定一个核心例子：电商库存与订单处理服务。

它会在不同章节里反复出现：

- 第 1 章：为什么库存明明只想减一次，最后却还能超卖。
- 第 2 章：为什么停售开关改了，工作线程却还在跑。
- 第 3 章：为什么库存扣减和订单状态更新需要互斥或同步协议。
- 第 4 章：为什么订单校验、创建、支付确认适合用线程池和异步编排。
- 第 5 章：为什么订单事件流适合放进阻塞队列。
- 第 6 章：为什么限流、批次会合和计数更新未必都靠锁。
- 第 7 章：为什么热点库存、线程池堆积和死锁会成为真实线上问题。

用同一个例子反复升级，有一个好处：你不会把每章当成孤立的知识点，而会持续看到“同一个系统在不同并发层面暴露出的不同问题”。

## 章节导航

### 第 1 章：并发为什么难，Java 为什么不能只靠单线程直觉

目录：
[ch01-why-concurrency-is-hard-and-where-java-steps-in](chapters/ch01-why-concurrency-is-hard-and-where-java-steps-in)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch01-why-concurrency-is-hard-and-where-java-steps-in/lesson-00-chapter-guide.md)

这一章解决“问题从哪里来”。重点是共享状态、竞态条件、原子性、可见性和有序性。

适合直接跳读：
如果你写过多线程代码，但总是把“线程安全”理解成“加锁就行”，先从这一章进最稳。

关键词：
线程、共享状态、竞态条件、原子性、可见性、有序性

读完本章后下一步：
→ 进入 [第 2 章](chapters/ch02-java-memory-model-and-volatile)，看 Java 内存模型怎样解释这些现象。

---

### 第 2 章：Java 内存模型、`volatile` 与可见性

目录：
[ch02-java-memory-model-and-volatile](chapters/ch02-java-memory-model-and-volatile)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch02-java-memory-model-and-volatile/lesson-00-chapter-guide.md)

这一章解决“为什么线程之间会看不见彼此的修改，以及 `volatile` 为什么既重要又不万能”。

适合直接跳读：
如果你经常看到 `volatile`，但说不清它和线程安全、原子性到底是什么关系，从这里开始。

关键词：
JMM、主内存、工作内存、可见性、`volatile`、重排序

读完本章后下一步：
→ 继续进入 [第 3 章](chapters/ch03-locking-synchronization-and-happens-before)，看互斥与同步怎样把共享状态真正管起来。

---

### 第 3 章：锁、同步与 `happens-before`

目录：
[ch03-locking-synchronization-and-happens-before](chapters/ch03-locking-synchronization-and-happens-before)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch03-locking-synchronization-and-happens-before/lesson-00-chapter-guide.md)

这一章解决“线程安全到底靠什么建立”，包括 `synchronized`、`ReentrantLock`、`Condition` 和同步语义。

适合直接跳读：
如果你最关心“到底什么时候该加锁、什么时候不该”，从这一章进入。

关键词：
`synchronized`、锁、互斥、`ReentrantLock`、`Condition`、`happens-before`

读完本章后下一步：
→ 继续进入 [第 4 章](chapters/ch04-thread-pools-futures-and-task-orchestration)，看线程从“共享状态保护”怎样走向“任务受控调度”。

---

### 第 4 章：线程池、`Future` 与任务编排

目录：
[ch04-thread-pools-futures-and-task-orchestration](chapters/ch04-thread-pools-futures-and-task-orchestration)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch04-thread-pools-futures-and-task-orchestration/lesson-00-chapter-guide.md)

这一章解决“为什么真实工程里不能随便开线程，以及任务怎样被安全地拆分、调度、组合”。

适合直接跳读：
如果你已经知道锁，但对 `ExecutorService`、`Future`、`CompletableFuture` 还比较散，从这里进入。

关键词：
线程池、任务模型、`ExecutorService`、`Future`、`CompletableFuture`

读完本章后下一步：
→ 继续进入 [第 5 章](chapters/ch05-concurrent-collections-and-producer-consumer)，看并发如何落到容器与队列协作。

---

### 第 5 章：并发容器与生产者-消费者

目录：
[ch05-concurrent-collections-and-producer-consumer](chapters/ch05-concurrent-collections-and-producer-consumer)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch05-concurrent-collections-and-producer-consumer/lesson-00-chapter-guide.md)

这一章解决“多个线程共享的已经不是一个变量，而是一批数据结构时，应该怎样安全协作”。

适合直接跳读：
如果你最关心 `ConcurrentHashMap`、`BlockingQueue`、事件驱动消费流程，从这一章进入。

关键词：
并发容器、`ConcurrentHashMap`、`CopyOnWriteArrayList`、`BlockingQueue`、生产者-消费者

读完本章后下一步：
→ 继续进入 [第 6 章](chapters/ch06-atomic-cas-and-coordination-primitives)，看锁以外的并发协调工具。

---

### 第 6 章：CAS、原子类与协调原语

目录：
[ch06-atomic-cas-and-coordination-primitives](chapters/ch06-atomic-cas-and-coordination-primitives)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch06-atomic-cas-and-coordination-primitives/lesson-00-chapter-guide.md)

这一章解决“哪些并发问题更适合用原子更新、计数器、闸门或线程会合来处理”。

适合直接跳读：
如果你经常听到 CAS、`AtomicInteger`、`CountDownLatch`、`Semaphore`，但只停留在 API 名字层，从这里进入。

关键词：
CAS、原子类、`CountDownLatch`、`CyclicBarrier`、`Semaphore`

读完本章后下一步：
→ 继续进入 [第 7 章](chapters/ch07-concurrency-design-performance-and-diagnostics)，看工具选择如何回到设计与排障。

---

### 第 7 章：设计、性能与诊断

目录：
[ch07-concurrency-design-performance-and-diagnostics](chapters/ch07-concurrency-design-performance-and-diagnostics)

建议入口：
[lesson-00-chapter-guide.md](chapters/ch07-concurrency-design-performance-and-diagnostics/lesson-00-chapter-guide.md)

这一章解决“并发代码上线以后，怎样判断它能不能扛、出了问题怎样查、为什么有些写法天生更难维护”。

适合直接跳读：
如果你最关心线上问题、线程池堆积、死锁和调优，从这一章进入。

关键词：
线程池参数、死锁、活锁、饥饿、锁竞争、排障、压测

---

## 当前文档结构

当前目录结构如下：

- `00-outline.md`：整套课程的大纲与章节递进关系
- `README.md`：当前这个入口页
- `chapters/`：按章节组织的正文与导学

当前已经完整展开第 1 章，后续章节导学已落位，可按同一条主线继续展开。

## 如何使用这套内容

如果你想从头系统学，按推荐顺序从 `00-outline.md` 一路读下去最合适。

如果你已经有基础，想快速定位某一部分：

- 想先看“并发为什么会出错”，从第 1 章开始。
- 想先看“`volatile` 到底能干什么”，从第 2 章开始。
- 想先看“锁和同步语义”，从第 3 章开始。
- 想先看“线程池和异步编排”，从第 4 章开始。
- 想先看“并发队列和容器”，从第 5 章开始。
- 想先看“CAS 和协调工具”，从第 6 章开始。
- 想先看“线上调优和排障”，从第 7 章开始。

如果你想先抓一条最短主线：

1. [第 1 章](chapters/ch01-why-concurrency-is-hard-and-where-java-steps-in)
2. [第 2 章](chapters/ch02-java-memory-model-and-volatile)
3. [第 3 章](chapters/ch03-locking-synchronization-and-happens-before)
4. [第 4 章](chapters/ch04-thread-pools-futures-and-task-orchestration)
5. [第 7 章](chapters/ch07-concurrency-design-performance-and-diagnostics)

## 一句话收束

如果你只想先记住一句课程总纲，那就记这句：

Java 并发编程，不是在学一堆并行工具，而是在学怎样让共享状态下的系统保持有序。
