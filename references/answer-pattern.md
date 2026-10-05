# Answer Pattern

Use this reference to calibrate structure, detail, and tone. Preserve the pattern, not the particular theorem, symbols, or example-specific knowledge assessment.

## Contents

- Reusable output skeleton
- Positive example: completed version of the user's handwritten solution
- Additional positive examples

## Reusable output skeleton

1. `解题前的知识准备`
   - List only the important prerequisites.
   - Mark the evidence-based mastery status and planned explanation depth.
2. `分析`
   - Recognize the structure and standard method.
   - Use the standard method to obtain a candidate target when helpful.
   - Identify why that shortcut is not yet rigorous.
   - Propose a natural theorem or route heuristically, without pretending its hypotheses are already proved.
   - Separate intuitive observations from uncertain points and possible failure modes.
   - Turn every uncertainty into a proof obligation for the solution.
   - Calibrate when and how deeply to discuss a local technique according to what would naturally be noticed; treat this as a degree judgment, not a rigid boundary.
   - Let the analysis equal or exceed the proof in length through method exploration, not by duplicating the formal calculations.
3. `解`
   - Treat exceptional cases first when needed.
   - For each main step, give the target, local method analysis, full derivation, and conclusion.
4. `补充知识`
   - Explain important tools whose mastery is unconfirmed or which the user explicitly has not learned.
5. Check that the proof closes every gap identified in the analysis.

## Positive example: completed version of the user's handwritten solution

### 题目

设 $a>0$，$p$ 为正整数，且

$$
x_1>a^{1/p}.
$$

数列由下式递推定义：

$$
x_{n+1}=\frac{p-1}{p}x_n+\frac{a}{p}x_n^{-p+1}.
$$

证明：

$$
\lim_{n\to\infty}x_n=a^{1/p}.
$$

### 解题前的知识准备

本示例根据用户给出的手写过程作如下判断；不得把这些判断沿用到其他用户或题目。

- **不动点法**：用户已经用它预先求出了候选极限，按已掌握处理；重点提醒它不能代替极限存在性的证明。
- **数学归纳法与单调有界定理**：手写过程和课程笔记中已有使用依据，按已掌握处理；分析阶段可以先把单调有界定理作为自然候选路线，但正式使用前必须在解题阶段证明它的条件。
- **AM-GM 均值不等式**：用户明确表示尚未掌握，因此在证明中解释选择原因，并在解答后单独补充。

### 分析

这是一个递推数列极限问题。首先可以用这类题的常见方法寻找候选答案，但此时不能决定最终采用哪条收敛路线。

假设数列存在极限，记其为 $A$，并把递推式两边取极限，则形式上有

$$
A=\frac{p-1}{p}A+\frac{a}{p}A^{-p+1}.
$$

把等式两边乘以 $p$：

$$
pA=(p-1)A+aA^{-p+1}.
$$

两边减去 $(p-1)A$：

$$
A=aA^{-p+1}.
$$

如果 $A>0$，两边乘以 $A^{p-1}$，得到

$$
A^p=a.
$$

因此候选极限是

$$
A=a^{1/p}.
$$

但这只是“先射箭后画靶”：它告诉我们极限如果存在，可能等于什么，却没有证明极限存在。因此接下来首先要想办法证明收敛。

对于实数列，最常见的收敛工具之一是单调有界定理，所以可以先尝试走这条路线。不过，这里只是根据题型和经验提出候选方法，并不是说数列已经被证明单调有界。

先凭递推式观察正性。题设给出

$$
x_1>a^{1/p}>0.
$$

当 $p>1$ 且 $x_n>0$ 时，递推式右边的两项都为正，因此直观上数列会一直保持为正数。由此至少可以预期它存在一个最粗略的下界 $0$。

真正不明显的是单调性。递推式右边既含有 $x_n$，又含有 $x_n$ 的负次幂；当 $x_n$ 变化时，这两部分的变化方向相反，所以不能只看形式就断言数列递增或递减。它也有可能越过候选极限，甚至在两侧震荡。

因此，若要尝试单调有界定理，正式解答中需要完成两个关键任务：

1. 找到一个对求极限有用的下界。候选极限 $a^{1/p}$ 很可能就是这个下界，但需要证明数列始终不会落到它下面。
2. 具体计算或比较 $x_{n+1}$ 与 $x_n$，确定数列是否真的单调；如果并不单调，就必须放弃这条路线并寻找别的方法。

对于第一个任务，因为要证明一个关于所有正整数 $n$ 的结论，而数列又由前一项递推得到，所以可以先尝试使用数学归纳法。归纳步骤中究竟应当怎样估计 $x_{n+1}$，目前从原式还看不清楚，应当进入正式解答后再根据变形结果寻找合适工具。

对于第二个任务，最直接的办法是计算

$$
x_{n+1}-x_n
$$

并判断其符号。但这个符号很可能还会依赖第一步得到的下界，所以证明顺序应当先下界、后单调性。

因此，当前得到的是一条待验证的解题路线：

1. 先处理 $p=1$ 的特殊情形。
2. 对 $p>1$，尝试用数学归纳法证明数列始终大于候选极限；归纳步骤所需的具体估计方法留到执行时寻找。
3. 在这个结论的基础上计算相邻两项之差，判断数列是否单调递减。
4. 如果前两项验证成功，再使用单调有界定理证明极限存在。
5. 极限存在以后，才能合法地使用前面得到的不动点方程求出极限。

### 解

#### 特殊情形：$p=1$

**本步目标：** 先处理递推式会直接简化的特殊情形。

当 $p=1$ 时，递推式变为

$$
\begin{aligned}
x_{n+1}
&=\frac{1-1}{1}x_n+\frac{a}{1}x_n^{-1+1}\\
&=0\cdot x_n+a x_n^0\\
&=a.
\end{aligned}
$$

因此从 $x_2$ 开始，数列恒等于 $a$，所以

$$
\lim_{n\to\infty}x_n=a=a^{1/1}.
$$

下面只需讨论 $p>1$。

#### 第一步：证明 $x_n>a^{1/p}$

**本步目标：** 为数列建立下界，并为后面判断差值的符号作准备。

**执行分析：** 归纳步骤要求我们从 $x_n>a^{1/p}$ 推出 $x_{n+1}>a^{1/p}$，所以需要把递推式右边与目标值比较。先把右边通分：

$$
x_{n+1}
=\frac{(p-1)x_n+a x_n^{-p+1}}{p}.
$$

单看这个分式仍不容易直接与 $a^{1/p}$ 比较。注意 $p$ 是正整数，分子中的 $(p-1)x_n$ 可以展开成 $p-1$ 个相同的 $x_n$：

$$
(p-1)x_n
=\overbrace{x_n+x_n+\cdots+x_n}^{p-1\text{ 个}}.
$$

代回以后，

$$
x_{n+1}
=\frac{\overbrace{x_n+x_n+\cdots+x_n}^{p-1\text{ 个}}+a x_n^{-p+1}}{p}.
$$

现在结构才清楚：分子一共有 $p$ 个正数，其中前 $p-1$ 个都是 $x_n$，最后一个是 $a x_n^{-p+1}$，整个分子再除以项数 $p$。所以它正是这 $p$ 个正数的算术平均。

直到这一步才自然想到使用 AM-GM。还需要检查它的几何平均能否产生目标值。上述 $p$ 个数的乘积是

$$
x_n^{p-1}\cdot a x_n^{-p+1}=a,
$$

因此几何平均恰好为 $a^{1/p}$。这说明 AM-GM 正好可以给出归纳步骤所需的下界；至于能否得到严格不等式，还要继续检查等号条件。

由题设，

$$
x_1>a^{1/p}.
$$

现在假设对某个 $n$ 有

$$
x_n>a^{1/p}.
$$

因为 $a>0$，所以 $a^{1/p}>0$，进而 $x_n>0$。把递推式写成 $p$ 个正数的算术平均：

$$
x_{n+1}
=\frac{\overbrace{x_n+\cdots+x_n}^{p-1\text{ 个}}+a x_n^{-p+1}}{p}.
$$

由 AM-GM 均值不等式，

$$
\begin{aligned}
x_{n+1}
&\geq \sqrt[p]{x_n^{p-1}\cdot a x_n^{-p+1}}\\
&=\sqrt[p]{a x_n^{(p-1)+(-p+1)}}\\
&=\sqrt[p]{a x_n^0}\\
&=a^{1/p}.
\end{aligned}
$$

还要判断这里能否取等号。AM-GM 取等号当且仅当这 $p$ 个正数全部相等，因此必须有

$$
x_n=a x_n^{-p+1}.
$$

因为 $x_n>0$，两边乘以 $x_n^{p-1}$，得到

$$
x_n^p=a,
$$

也就是

$$
x_n=a^{1/p}.
$$

这与归纳假设 $x_n>a^{1/p}$ 矛盾，所以等号不成立，从而

$$
x_{n+1}>a^{1/p}.
$$

结合初始条件，由数学归纳法可知，对所有正整数 $n$，都有

$$
x_n>a^{1/p}.
$$

**本步结论：** 数列以下界 $a^{1/p}$ 为严格下界，并且所有项都为正。

#### 第二步：证明数列严格单调递减

**本步目标：** 证明相邻两项之差为负，以便应用单调有界定理。

**执行分析：** 要判断单调性，最直接的方法是计算 $x_{n+1}-x_n$。第一步已经得到 $x_n>a^{1/p}$，所以 $x_n^p>a$；我们希望把差值整理成含有 $a-x_n^p$ 的形式，这样就能立即判断符号。

由递推式，

$$
\begin{aligned}
x_{n+1}-x_n
&=\frac{p-1}{p}x_n+\frac{a}{p}x_n^{-p+1}-x_n\\
&=\left(\frac{p-1}{p}-1\right)x_n+\frac{a}{p}x_n^{-p+1}\\
&=-\frac{1}{p}x_n+\frac{a}{p}x_n^{-p+1}\\
&=\frac{1}{p}\left(-x_n+a x_n^{-p+1}\right)\\
&=\frac{1}{p}\left(-\frac{x_n^p}{x_n^{p-1}}+\frac{a}{x_n^{p-1}}\right)\\
&=\frac{a-x_n^p}{p x_n^{p-1}}.
\end{aligned}
$$

由第一步，

$$
x_n>a^{1/p}.
$$

因为 $p$ 是正整数且两边均为正，所以

$$
x_n^p>a.
$$

因此分子满足

$$
a-x_n^p<0.
$$

同时 $p>0$ 且 $x_n>0$，所以分母满足

$$
p x_n^{p-1}>0.
$$

于是

$$
x_{n+1}-x_n<0,
$$

即

$$
x_{n+1}<x_n.
$$

**本步结论：** 数列严格单调递减。

#### 第三步：证明极限存在

**本步目标：** 补上分析阶段使用不动点法时缺失的关键前提。

第一步证明了数列有下界 $a^{1/p}$，第二步证明了数列单调递减。因此，由单调有界定理，数列 $(x_n)$ 收敛。记

$$
\lim_{n\to\infty}x_n=A.
$$

而且由

$$
x_n>a^{1/p}>0
$$

可知

$$
A\geq a^{1/p}>0.
$$

**本步结论：** 极限 $A$ 确实存在且为正，现在可以合法地对递推式取极限。

#### 第四步：利用不动点方程求极限

**本步目标：** 求出已经证明存在的极限。

因为 $A>0$，函数 $t\mapsto t^{-p+1}$ 在 $A$ 附近连续。对递推式两边取极限：

$$
\begin{aligned}
A
&=\frac{p-1}{p}A+\frac{a}{p}A^{-p+1}.
\end{aligned}
$$

等式两边乘以 $p$：

$$
pA=(p-1)A+aA^{-p+1}.
$$

两边减去 $(p-1)A$：

$$
A=aA^{-p+1}.
$$

因为 $A>0$，两边乘以 $A^{p-1}$：

$$
A^p=a.
$$

正数范围内方程只有一个解，因此

$$
A=a^{1/p}.
$$

所以

$$
\boxed{\lim_{n\to\infty}x_n=a^{1/p}}.
$$

### 补充知识：为什么使用 AM-GM

对任意 $p$ 个正数 $y_1,y_2,\ldots,y_p$，AM-GM 均值不等式为

$$
\frac{y_1+y_2+\cdots+y_p}{p}
\geq
\sqrt[p]{y_1y_2\cdots y_p}.
$$

等号成立当且仅当

$$
y_1=y_2=\cdots=y_p.
$$

本题递推式中的权重分别是 $(p-1)/p$ 和 $1/p$。把第一项拆成 $p-1$ 个相同的 $x_n$ 后，递推式就变成 $p$ 个正数的算术平均。对应关系是：

$$
y_1=\cdots=y_{p-1}=x_n,
\qquad
y_p=a x_n^{-p+1}.
$$

选择 AM-GM 的关键不是“看到加法就套不等式”，而是乘积会发生精确抵消：

$$
y_1y_2\cdots y_p
=x_n^{p-1}\cdot a x_n^{-p+1}
=a.
$$

所以几何平均恰好等于目标下界 $a^{1/p}$。这解释了为什么该不等式既能证明下界，又能把下界直接对准分析阶段猜出的候选极限。

## Additional positive examples

- [Oscillating recurrence resolved through odd and even subsequences](oscillating-recurrence-example.md): use this when a one-step recurrence reverses order, early terms oscillate, or a two-step map reveals monotonicity hidden from the original recurrence.
