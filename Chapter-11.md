# 第十一章：博弈论

### 递归

* 20世纪最具影响力的经济学家凯恩斯（Keynes）说过“成功的投资是预料别人预期什么。”

Successful investing is anticipating the anticipations of others.

* 股票的价值不在于我们认为它值多少，而是我们认为别人认为它值多少。

* 图灵1936年证明停机问题：电脑程序永远无法明确告诉我们，另一个程序是否会永无止境地计算下去。同样地，程序员不可能设计出自动化工具，告知他们设计的软件是否有bug。进而简单来讲，在任何时候，一个系统（无论是机器或思想）模拟复杂程度本身相仿的事物时，会发现本身的资源几乎完全用尽。

* 棋牌游戏是从算牌到算人的过程。

### 纳什均衡，就是博弈达到均衡

* 纳什均衡：双方了解规则后互相角逐，找出一套双方遵循并且即使让双方知道对方的行动后，也不会改变本身行动的策略。均衡是因为很稳定，也就是双方即使再怎么考虑都不会改变自身选择。

* 纳什均衡分为纯策略均衡和混合策略均衡。前者如囚徒困境，后者如剪刀石头布游戏。

* 纳什在1951年证明所有2人博弈至少有一个均衡状态。参与者数目与策略数目均有限的博弈，至少有一个混合策略均衡。

* 数学研究的是事实（存在性）；电脑科学研究的是复杂性，例如如何（有效率地）找到（最优）解。

* 纯粹寻找纳什均衡同样是难解问题，为PPAD完全问题。

* 虽然PPAD完全问题没有NP完全问题那么糟，但目前大多数人认为很难有有效解法。如果一个均衡概念无法有效计算，那么它预测理性参与者行为的可信度将会大打折扣。

* 算法博弈论书籍《Algorithmic Game Theory》 Nisan et al.

### 优势策略，无论如何都要这么做

* 纳什均衡策略只是稳定，即所有参与者都不愿意改变行动的状态，但不一定是可以让所有参与者都获得最佳结果的策略。如囚徒困境，各人依据自身利益采取理性行动，得到的均衡明显不是最好的结果。

* 自主行为代价（price of anarchy, POA, 无秩序代价）度量可衡量合作和竞争两者间的差距。合作指集中设计或协调的解决方案；竞争指所有参与者各自试图取得对自己最好的结果。

* 人类通行方面，自主行为代价甚低有好处也有坏处。好处是缺少中央协调但最多只会让通勤时间增加 1/3。另一方面，自动驾驶汽车各行其是，不可能有大的提高，且已接近最佳状态。经过完美协调后的拥塞程度也只能提高到现在的 3/4。即现在的状态也只是最佳状态的 3/4。

* 自主行为代价很低，代表本系统无论是否细心管理，运作状况都和放任差不多。反之，代价越高表示管理价值越高，如果没有任何介入，可能造成灾难。囚徒困境就属于后者，而且很多都这样。

### 公共地悲剧

* 公共地悲剧等都会陷入糟糕状况。令这类恶性均衡维持稳定（使它们均衡）的正是最糟糕的特质。无法从内部改变优势策略（优势策略驱使大家走向糟糕），但这不表示这类恶性均衡无法矫正，而只表示我们应朝外部寻求解决方案，改变博弈规则（机制设计）。

### 机制设计：改变博弈

* 博弈论探讨在一定规则下会出现什么行为，而机制设计（也称逆向博弈论）则是反其道而行，探讨什么规则会产生我们希望的行为。当博弈规则迫使提出不好的策略，或许不应该试图改变策略，而是应该试图改变博弈。

* 将均衡状态收益降低到参与者接受不了的程度，强制均衡变为合作（大家都希望的最佳策略）。更直接的是，虽不改变均衡收益，但有外部对执行此策略的人进行处罚，如合约等。

* 宗教本身就是修改博弈架构的一种直接方法。宗教施行的行为限制缩减我们的选项数，不只可以降低某些决定在运算上的困难，还可以产生更好的结果。

* 书籍《Things a Computer Scientist Rarely Talks About》 D. E. Knuth讨论了电脑科学家很少谈到的事情。

### 演化进行的机制设计

* 树木竞相长高就是类似公共地悲剧的情况。只有长高才能不被其他树木遮住阳光，才能更好地生长。虽然长高大会使很多能量浪费在树干上。

* 如果群体与个体利益对所采取的策略表现不一致时，有时群体利益会胜出，而个体利益被忽略。这其中外部因素起了作用，如情绪超越了理性，使得参与者采取不利于自己但利于群体的策略。这在物种演化过程中起到了作用。

* 道德是个人心中的群居本能。情绪是物种的机制设计 -尼采。

* 诉讼是已开发社会中一种自我毁灭的报复方式（耗费时间精力金钱），而不是取代方案。

* 康奈尔大学经济学家Robert Frank曾说，如果知道让两人在一起的因素本来就不是理性思考，就不会担心对方会因为觉得结束关系比较理性而离开。

* 快乐本身即是桎梏。

### 信息瀑布：悲惨的理性泡沫

* 2014年google的收益中有90%以上来自广告。

* 拍卖：
1. 首价密封投标式拍卖（sealed-bid first-price auction）：（假设每个人对物品的估值是随机平均的）2个人投标时，均衡策略是投心中物品价值的1/2；一般地，n个人投标的拍卖中，投下的标金是心中物品估值的(n-1)/n。
2. 荷兰式拍卖（Dutch auction，也称递减式拍卖descending auction）：付出接近可接受范围内的最高价时投标。
3. 英国式拍卖（English auction，也称递增式拍卖ascending auction）：竞争加价直至只剩一家为止。
4. 维克里拍卖（Vickrey auction）：以密封式写下投标金额，价高者得，但付的是第二高的标金。此方法会鼓励参与者诚实，因其均衡就是心中的真实估价投标。故维克里拍卖被认为是不受策略影响或或者说是真实，诚实是占优策略。它以最佳方式隐藏标金。由收益等值（revenue equivalence）理论可知，经过一段时间后首价拍卖的平均期望出售价格将收敛到与维克里拍卖完全相同。

* 信息瀑布（information cascade，也称信息级联）：在适当的环境下，一群虚伪完全理性及合宜的参与者，仍然可能受无限的错误信息左右。

* 信息瀑布是很多风潮和群众行为以及泡沫的原因，它说明即使市场中没有非理性、恶意或违法行为，却也很容易飞涨和暴跌：
1. 留意公开信息似乎多于私人信息的状况，每人都偏重共识而非事实。
2. 记住人未必会根据想法行事，而是依据他人的行动错误解读他们的想法。
3. 应该从囚徒困境学到并记住，博弈规则有时糟糕的无药可救。

* 从机制设计和演化两方面思考。一般说来，特定个人最好是谨慎的从众者，但群体中有些成员持不同意见则往往可使所有人收益。因此，过度自信可以视为某种利他行为。这类人的最佳比例与过度自信的程度、信号精度、群体规模三个因素有关（文献“On the Evolution of Overconfidence and Entrepreneurs” Bernardo & Welch），但很难得出解析解。

### 忠于自己

* 机制设计不仅要考虑博弈的结果，还要考虑到参与者必须付出的运算能力。

* 诺奖学者Roger Myerson在揭示原理（revelation principle）中证明必须借助策略掩盖事实的博弈，都可转化成只需要诚实就好的博弈。

* 采取不需要因其它人的战术而预期、预测，深入了解或改变行动的策略，是直接解开递归死结的一种方法。这种策略有时不见得简单，却是最佳方法。

# 结语

* 在特定假设下，以最少硬币找零问题为NP困难。如果硬币面额为二进位或十进位，结果依然相同。但如果是一进位则有有效解。

“Two NP-Complete Problems in Nonnegative Integer Programming”, Lueker

“The Change-Making Problem”, Wright

“Optimal Bounds for the Change-Making Problem”, Kozen & Zaks