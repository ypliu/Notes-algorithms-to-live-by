# 第五章：排程（Scheduling）-优先的事优先处理

### 如何花时间

* 强森对洗衣和烘干（各次的洗衣时间和烘干时间可能并不相同），以总执行时间最少为目标。排程方法是**从两端排到中间的顺序**，开始执行最简单的清洗（最短洗衣时间），最后处理烘干量最少的衣服（最短烘干时间）。

### 在期限内完成最重要

* 拟定计划前，必须先选择测量标准（目标函数），这也是计算机科学的主题之一。

**策略**：
1. 如果希望尽可能**减少最大延迟**，最佳策略是最早到期日（Earliest Due Date, EDD），一开始先处理期限最早的工作，逐步处理到期限最晚的工作。
2. 如果以尽量**减少腐坏食物数量**为目标，摩尔-霍格森演算法是最佳策略，依腐坏顺序排序，最早腐坏的先吃，之后如果有没办法及时用掉的食物就放弃所需时间最长的食物。

* 不在乎已经延时的工作如何执行，因为已经剔出主要时程的计划可在最后依任何顺序执行，因为反正已经迟了。如晚点的火车就会被安排频繁停车让车。

### 如果划掉待办清单上越多越好

* 不可能改变完成所有工作所需的时间，但可以通过安排加工顺序来缩减完成总时间（自开始加工时计算各项工作的完成时间总和，sum of completion time）。

**策略**：
3. 最短处理时间（shortest processing time, SPT）：永远处理能最快完成的工作。
4. 对于加权情况，对单位时间重要性（权重/完成所需时间）降序，依次进行。

### 清楚评价成果的标准

* 拖延是可能是为了尽快减少心中待办事项数目而选择次要事物，却将重要事物一直延后。但真正评价标准是事物重要性，所以这是由于评估标准不同造成的。所以应该先处理最重要的工作。

### 优先权反转与优先权约束

* 当高优先级工作因低优先级工作阻碍停止（优先级反转，priority inversion）时，就要将此低优先级工作调高优先级（优先级继承，priority inheritance），成为优先事务执行。否则，可能会因中间工作导致原事务不能执行，原高级事务无法进行而造成死锁。

**策略**：
5. 以缩小一连串工作最大延迟程度为目标，对于有优先权限制（有依赖关系）以缩减最大延迟程度为目标的排程，罗勒（Lawler）1968年证明，从后往前只看不影响其他工作的未排定时程，**将到期日最晚的放在最后**，依此方法执行至所有工作。
6. 以尽快减少待办事项为目标，无优先权限制时，最短处理时间（SPT）为最佳策略，但有优先限制时，它就变成了 **NP-Hard**。

### 抢占与不确定性

* 抢占（preemption），工作可以中途停止，改做另一项。

**策略**：
7. 对于有特定时间启动限制，减少最大延迟和减少完成总时间都会变成**难解问题**。
8. 对于有特定时间启动限制，如果允许抢占，可以用调整的**最早到期日（EDD）减少最大延迟**，或**最短处理时间（SPT）减少待办事项**策略重新获得有效解。在启动时间时暂停，考虑新启动任务比当前正在执行的更优就抢占执行，否则继续原工作。

* 探讨不确定性影响时，有时预知反而成了负担，即使事前完全知道状况可能同样无法知道完美排程。此时把计划换成猜测，轻松面对就好。

### 插队的代价：上下文交换

* 切换次数越多，间接成本越高。

### 忙到变成空转：往复移动

* 切换工作造成的往复移动，系统会完全被内耗占据而停顿。此时总想执行最优可能耗费更大。

### 错过这次，就等待下回-中断接合

* 设定最小执行时间有助于防止为确保反应能力而频繁切换造成不能很好地处理事务。

* 中断接合（interrupt coalescing）等到某固定时间才检视，而不是经常执行上下文切换处理所有的个别中断。

* 定期会议尽管有很多诸多缺点，却是防范无意识中断和规划外上下文切换的最佳方法。
