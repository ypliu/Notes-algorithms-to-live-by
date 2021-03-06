# 第一章：停止问题

### 非完全信息

* 一般情况下的非完全信息遴选问题（秘书问题，对方不会拒绝，也不能回头找面试过的人选），以最大概率找到最优秀候选为目标。

**策略**：将前面一部分作为考察对象评估整体水平，但不录取（炮灰）。其后一旦出现比之前都优秀的就直接录取，后面的不再面试。

考察前 $\frac{1}{e} \approx 36.79%$ 为基准，但不录取，其后一旦遇到比他们优秀的就录用并停止，如此可以达到 $\frac{1}{e} \approx 36.79%$ 概率录用到最佳人选。

如果是录用时对方有 50% 拒绝的可能性，就要在考察前 25% 后就开始录用找到的最佳，如果被拒绝就继续，如此录用到最佳人选的概率也是 25%。

如果录用不会被拒绝，而允许回头但 50% 可能会拒绝，则要经过 61% 人选考察，其后开始录用最佳者。如此录用到最佳人选的概率也是 61%。

**结论**：允许回头录取时被接受的概率为 p，为录取当前时的概率 q，则起初跳过的考察人选为 $(q^2/q-p^{1-q})^{1/(1-q)}$。

* 不允许回头录取的非完全信息秘书问题**数学模型**

假设共有n个候选，将前x个作为参考基准，之后一旦遇到比前x个都优秀的就录取。这样就要求最优秀候选的序号是在$[x+1, n]$中，且在它之前的第二优秀候选必须在前x个参考基准中（条件概率），否则此第二优秀候选就被选成答案。

```math
p = \sum_{i=x+1}^n \frac{1}{n} * \frac{x}{i-1} \stackrel{j=i-1} = \sum_{j=x}^{n-1} \frac{x}{n} * \frac{1}{j} \overset{t=\frac{j}{n}}{=} \sum_{t=\frac{x}{n}}^{1-\frac{1}{n}} \frac{x}{n} * \frac{1}{nt} \overset{y=\frac{x}{n}}{\longrightarrow} y \int_{y}^{1-\frac{1}{n}} \frac{1}{t}\, dt \overset{n \to \infty}{\longrightarrow} y \int_{y}^{1} \frac{1}{t}\, dt = y * \ln t \big|_y^1 = -y * \ln y
```
```math
p^\prime = -(\ln y + y * \frac{1}{y}) = -(\ln y + 1) = 0 \Longrightarrow y = \frac{1}{e}, p = \frac{1}{e}
```

### 完全信息

* 如果是完全信息遴选问题（知道对方的整体分数排名），以找到最优秀候选为目标。

**策略**：临界值法则（Threshold Rule）。使用逆向归纳法，根据所剩余的人数，计算后续人选的平均分数，一旦当前人选超过此期望就录取并停止面试，否则就面试下一位。

即，不需要观察人选来设定临界值，但要清楚还有多少人可以选。候选人少就降低标准，候选人多久提高标准。

倒一：没得选，只能录取。倒二：是否达到 50%（倒一的期望值，且达到的概率是 50%），没超过就继续跳过看倒一。倒三：是否达到 69%。倒四：是否达到 78%。。。绝不录用低于平均水准的人选。这样找到最优人选的几率是 58%。

* 何时出手自己的物品，以净胜值为目标。

**策略**：考虑下一次的出价同时，要注意等待成本多少。即达到当前的计算临界值就结束，否则继续等待。将出价区间正则到 [0,1]，当前价格 p 和等待出价成本 c，下次出价高于 p 的概率为 1-p（则下一次出价高于 p 的期望 $\frac{1-p}{2}$）。当 $(1-p) \frac{1-p}{2} \ge c$ 时继续等待，否则 $p \ge 1-\sqrt{2c}$ 时出售。

例如，售价为40-50万的房屋，等待成本2千。临界值 $p' \ge 1-\sqrt{2*\frac{0.2}{50-40}}=0.8$，即临界出价 $p = 40 + 10 * 0.8 = 48$。

### 何时停车问题

* 停车问题：根据目标车位空置率决定如何停车。

**策略**：根据空置率 p 计算距目标剩余 $-log2/log(1-p)$ 个车位时，一旦遇到空位就停车。

占有率由90%提高到95%时，找车位的时间会变成两倍。

### 何时见好就收

* 何时见好就收

某生意成本为 c，能以概率 p 赚取 d 元，但一旦失败（概率1-p）输掉所有。那么最多连续成功（最小的r） $p^{r/d+1} \le c/d$ 次就要罢手。

如果成功率是 p 的某行动获利 m，但一旦失败就彻底毁灭。那么只能执行最多 $p/(1-p)$ 次行动。

三倍或输光，第一局期望收益1.5，赢了后的第二局期望收益4.5，但从数学上看，是一直玩。但有些问题不去管它要比解决它来得好。

### 教科书

最优停止问题的权威教科书 Optimal Stopping and Applications by Thomas S. Ferguson（https://www.math.ucla.edu/~tom/Stopping/Contents.html）

### 凯利公式

* 凯利公式（Kelly criterion）

+ https://xueqiu.com/4105947155/66889413
+ https://wallstreetcn.com/articles/3235993

真正应该关心的是长期累积的收入，对于累积的收益来说，按比例投资最后的结果只和输赢的局数有关，而和输赢的顺序无关。

**简单形式**：胜几率 p，赔率 b（6倍回报->1赔(p=)5），则每次投入比例
```math
f=\frac{p*b-q}{b}=\frac{p(b+1)-1}{b}
```
，使得整体收益最佳。

赢面、预期获益 edge = bp-q；赔率、获益回报 odd = b；bet = edge/odds = 预期获益／获益回报

**变形**：考虑收益率损失率情况下的投入比例
```math
f=\frac{p*r_w-q*r_l}{r_w*r_l}=\frac{p}{r_l}-\frac{1-p}{r_w}
```
，使得整体收益最佳。其中赚钱概率p、赔钱概率q=1-p，净收益率$r_w$=最高价/当前价-1，净损失率4r_l$=1-最低价/当前价。

* 凯利公式推导

考虑第k+1轮：
> 如果成功，总额为
```math
A_{k+1} = A_k(1+f*r_w)
```
> 如果失败，总额为
```math
A_{k+1} = A_k(1-f*r_l)
```

进而在N次之后总额期望为
```math
A_N = A_0(1+f*r_w)^{Np} * (1-f*r_l)^{N(1-p)}
```
则单次的期望收益比例为
```math
F(f) = \sqrt[N]{\frac{A_N}{A_0}} = (1+f*r_w)^{p}*(1-f*r_l)^{1-p}
```

将要优化的原始目标函数做如下转换：
```math
g=\ln{F(f)}=p*\ln(1+f*r_w)+(1-p)*\ln(1-f*r_l)
```
求导置零得答案。且资金增长率
```math
r=e^g-1
```

### 巴菲特投资优化公式

* 巴菲特投资优化公式

《巴菲特的投资组合》，$x = 2p - 1$。其中，p：成功的概率、x：投入的资金百分比。
