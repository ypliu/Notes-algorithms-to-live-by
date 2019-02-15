# 第九章：随机性

### 什么时候该让概率决定

* 处理困难问题时，随机性算法有时可以比各种已知的确定性算法更快提出不错的（近似）答案。

### 抽样

* 蒲丰投针实验：若针长比线的间隔短，则相交的概率为
```math
p = \frac{2l}{d\pi}
```
，其中l、d为针长和线的间隔。

* 拉普拉斯：如果想了解某个复杂的性质，可以藉由抽样估计它的值。

* 蒲丰投针计算：

### 费米估算问题

将大的问题化整为零（从上至下或从下至上），计算过程中以均值方式，且在整个过程中去除误差。当然前提是必须能够得知某些基础数据。

### 随机化演算法

* 现代加密技术的出发点就是大整数的质数分解困难，虽然相乘容易计算（单向函数）。这样即使此用于加密的合数公开也不用担心密钥被破解。

* 质数检验：
1. Gary Miller博士论文中提出n的质数性检验演算法，参数x：当n为质数时，无论x为何值，检测函数一定为真；而当某一x对应的检测函数为假时，n一定是合数；
2. 若广义黎曼假设为真，则必须检测的个数为 $O(log^2 n)$；
3. Michael Rabin发现，若n为合数，不超 1/4 的x会使判断为真；
4. 以k个不同的x执行上面验证步骤，则均为真而n为合数（判断失败）的概率为 $(\frac{1}{4})^k$；
5. FIPS数字签名标准（DSS）接受的误差概率为 $2^{-80}$（40次MR检测）；
6. Miller-Rabin检测算法伪代码[^1]：
```pseudocode
Input #1: n > 3, an odd integer to be tested for primality;
Input #2: k, a parameter that determines the accuracy of the test
Output: composite if n is composite, otherwise probably prime

compute n−1 = 2^r*d with d odd by factoring powers of 2 from n−1
WitnessLoop: repeat k times:
    pick a random integer a in the range [2, n − 2]
    x \leftarrow a*d mod n
    if x == 1 or x == n−1 then
        continue WitnessLoop
    repeat r−1 times:
        x \leftarrow x^2 mod n
        if x == n−1 then
            continue WitnessLoop
    return composite
return probably prime
```

* 《Primer is in P》，印度师生证明了质数检验是多项式问题。

* 两多项式相等验证也是随机算法:取多个x值计算函数值是否相等。依代数基本定理：如果两次均为一元n次，则n+1个x值可明确判断。

### 礼赞抽样

* 无知之幕（veil of ignorance），在即将发生而未发生之时刻，想象会处于何种情形，而人们在无知之幕后方评估各种社会状况之后，应该会对理想社会的样貌更有共识。

* 要理解一个过于复杂，无法直接理解的事物，仔细研究随机样本可能是最有效的方法，抽样因此重要。

* 抽样要保证公平，不能是刻意挑选。

### 取舍“确定程度”-电脑给的答案不一定对

* 布隆过滤器（Bloom Filter）：在容许一定错误（大约1%-2%）前提下，将key代入一个散列函数集合，当所有函数检验均为真时，就表明该key存在。从而实现对时间和空间的大量节约。误差权衡空间，避免搜索中耗时。

### 离开局部最大值

* 破解电码就使用了多次随机重启策略。

* 引入随机化，希望解能够跳出局部最优，趋向更好的解。

### 模拟退火

* 退火过程中，以递减概率接受较差解的做法和“开发与善用”权衡原理相似，起初是开发多看选择尝试；后期则是主要接受优良解的善用，且概率随时间的**对数**函数增加。

* 模拟退火（Simulated Annealing, SA）：以完全随机得到初始解（高温状态，解可能很差）；接着调整解（可能是局部搜索），如果变得更好直接接受，而变得更差就依某一概率接受（且此概率随时间而变小），即冷却过程；直至局部最大解无法再改进为止。该论文发表在《Science》上，以物理学解决集成电路布局实际问题。

* $\epsilon / N$贪心法玩多臂土匪机可确保失败次数呈对数增加。在第n次选择时，以 $1/n$ 概率去尝试新的选择，否则就坚持目前找到的最佳选择。最后到达开发与善用的平衡点。Peter Auer, Nicolo Cesabianchi, Paul Fischer《Finite-Time Analysis of the Multiarmed Bandit Problem》。

* 汤普森取样（Thompson Sample）：使用贝叶斯法则计算每种选择是最佳选择的概率，再依概率决策。开始时等概率随机选择，随着资料增多，能够明确哪种更好时就固定下来。Thompson《On the Likehood That One Unknown Probability Exceeds Another》及Shipra Agrawal, Navin Goyal《Analysis of Thompson Sampling》。

### 随机性、演化和创造力

* 1940年代，鲁瑞亚（Luria）通过培养几代不同谱系细菌，再让最后一代接触病毒，结果数量很不平均，所以细菌是随机偶然的突变产生对病毒的抵抗力。因为如果抵抗力是对病毒的反应，则不论哪个谱系，每个培养基中有抵抗力的细菌应大致相同。相反如果抵抗来自偶然的突变，数量会很不平均。因为随机，先产生这种突变的菌落会有大量后代具有抵抗力，而后产生甚至没有突变的则很少有抵抗力。

* 盲目变异和选择性保留过程，是各种归纳性成就、各种真实知识增长，以及各种系统与环境适合程度增长的基础。

* 随机抖动、跳出框架，放眼更大尺度，离开局部最优，继续追寻整体最优。

---

MR素性检验代码实现参考
+ http://www.cnblogs.com/vongang/archive/2012/03/15/2398626.html
+ https://blog.csdn.net/alps1992/article/details/51588971
+ http://www.itdaan.com/blog/2018/04/22/b8da4520c5e4ac4466dbffbd98a55858.html
+ https://blog.csdn.net/tengweitw/article/details/23952839
+ https://blog.csdn.net/forever_dreams/article/details/82314237


[^1]: [wikipedia](https://en.wikipedia.org/wiki/Miller%E2%80%93Rabin_primality_test#Computational_complexity)
