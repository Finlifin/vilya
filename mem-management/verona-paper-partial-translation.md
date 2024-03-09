## 3 Reggio Regions
在这部分中，我们描述了Reggion区域系统的核心概念： 区域(regions), 区域拓扑逻辑，
区域上的操作，单可变窗口，和区域系统的属性。但是首先，让我们先预览一遍这些工作的目标

### 3.1 Motivation
本论文中的设计决策由以以下几点为目标：
+ 可控可预测的内存管理开销。
+ Mix-and-Match Memory Management?
+ 增量内存管理
+ 零复制