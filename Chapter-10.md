# 第十章：网络

### 我们如何互通信息

* 人类互通信息的基础是协议，也就是程序和预期的共通惯例，通讯也如此。

### 分组交换-为了非连续交谈而创

* 电话的回路交换是系统在传送者和接收者间开启一条通道，通话期间提供双向固定频宽。非常适合人类互动，但不适合机器的沟通。因为网络流量趋向某一方占主且有间歇特点。

* 分组交换不使用专属通道，而是把信息切割成小的数据包，然后在共有流中传递分发。

### 响应-怎么知道信息有没有送达

* “拜占庭将军问题”表明要满足一连串逻辑需要无限多则信息，通讯是唯一实际的解决办法，但理论上是不可能的。

### 指数退让-宽恕的演算法

* Abramson在1970年ALOHAnet的报告《The ALOHA system》指出，无线电波的平均利用率略高于 18.6% = 1/2e。

* 位于布局不明、争相发送的对话数目不明、无法得知且不断改变的网络中传输端点，只有一种方法可能顺利运作，就是指数退让。

* 电脑浏览网页失败后重连以及防字典攻击破解在密码失败后锁定时间指数延长都是指数避让策略。

* 美国司法部对缓刑者再犯的统计结果表明指数退让的有效性。

### 控制流量和避免拥塞

* 遇到得在不确定和不断变动环境下分配有限资源时，加法递增乘法递减（AIMD）是个方法。

* 彼得原理：所有员工通常会升到无法胜任的职位。因为能胜任就继续升迁，一旦升到无法胜任职位，就停止升职一直待在此职位。最终所有职位均由不适任的人占据。1910年加赛特（Gasset）提出每个公仆都应降一级，因为他们都升到了无法胜任的职位。

* 在无法预料且不断变化的环境中，要充分运用全部资源，最好（甚至唯一）的方法就是把状况推到出现错误。最重要的是确定错误反应迅速，而且很快就能恢复。

* 彼得原理的原因：阶级人生中最重要的守则-阶级必须维持。

### 秘密管道：语言学中的流量控制

* 发言的人和听众都同时参与说与听，因为有秘密管道（back channel）存在。这是协同行为，而非表面上的单向沟通。发言的人通过管道接收“是”、“嗯”等但没交出发言权。

* 对话中聆听者不明显的“是”、“嗯”、“哦”等简短反馈对于调节说话者到聆听者的资讯流量（包括速率和详细程度等），扮演着清楚明确的角色。如同网络TCP协议的ACK一样。所以教师讲课时要有学生反馈才能更好。

### 缓冲爆满-笨蛋，问题出在延迟

* 缓冲区必须要定期清空，才能有效运作。缓冲区过大可能会造成积存过大而整体延迟，拖慢全部网络工作。所以队列要小于处理能力。当队头数据包处理不了时，后面的也只能等待，这样队列越来越长，均是停滞状态。

### 既然迟了，不如就别做了

* 电子邮件也属于缓冲区，人们可以延后在闲适时处理。防止闲置。

* 减少延迟和频宽都是网络提高质量的主题。