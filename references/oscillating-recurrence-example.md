# Positive Example: Oscillating Recurrence

Use this example to calibrate how to preserve a realistic discovery path when the original sequence oscillates and monotonicity becomes visible only after separating parity. Preserve the reasoning pattern and explanatory depth, not the particular constants or conclusions.

## Problem

Let

$$
x_1=1,qquad x_2=\frac12,qquad x_{n+1}=\frac{1}{1+x_n}.
$$

Find

$$
\lim_{n\to\infty}x_n.
$$

## 解题前的知识准备

本示例中的知识状态只用于还原产生该答案时的上下文，不得沿用到其他用户或题目。

- **递推数列的不动点法**：用于先猜候选极限，但不能代替收敛性的证明。
- **单调有界定理**：可以作为首先尝试的常见路线，但原数列是否单调必须先检查，不能预设。
- **奇偶子列**：当递推映射会把不等号方向翻转、数列呈交替变化时，用它拆开震荡。

## 分析

这是一阶递推数列极限问题。先按照同类题的常见做法，用不动点方程寻找候选答案。

假设极限存在，并记为 $L$。形式上在递推式两边取极限，得到

$$
L=\frac{1}{1+L}.
$$

逐步整理：

$$
L(1+L)=1,
$$

$$
L^2+L-1=0.
$$

解二次方程：

$$
L=\frac{-1\pm\sqrt5}{2}.
$$

由递推式可以直观地看出各项为正，因此如果极限存在，只可能取正根

$$
\alpha=\frac{\sqrt5-1}{2}.
$$

但这里仍然只是“先射箭后画靶”：我们假设了极限存在，却尚未证明数列收敛。

接下来先看前几项，判断最常见的单调有界路线是否能直接使用：

$$
x_1=1,qquad x_2=\frac12,qquad x_3=\frac23,qquad x_4=\frac35.
$$

数列先下降、再上升、再下降，原数列不像是单调的。因此不能直接对整个数列使用单调有界定理。

这时观察递推函数

$$
f(x)=\frac{1}{1+x}.
$$

分母随 $x$ 增大而增大，所以 $f$ 会把大小关系反转。一次迭代反转一次，连续两次迭代就可能恢复原来的方向。这提示我们把奇数项和偶数项分开，研究二步递推。

因此正式证明计划是：

1. 证明所有项为正，确保递推式始终有意义。
2. 研究每一项位于候选极限 $\alpha$ 的哪一侧，说明奇偶项交替分居两侧。
3. 写出二步递推式，分别证明奇数子列和偶数子列单调。
4. 用两条子列彼此提供界，应用单调有界定理证明它们分别收敛。
5. 求出两条子列的极限，并由两者相同推出原数列收敛。

## 解

### 第一步：证明数列各项为正

**本步目标**：保证递推式中的分母恒为正，并为后面的不等式变形提供条件。

**执行分析**：初值为正；若某一项为正，则分母大于一，下一项仍为正，因此适合用数学归纳法。

**详细推导**：初始两项满足

$$
x_1=1>0,qquad x_2=\frac12>0.
$$

假设对某个 $n$ 有

$$
x_n>0.
$$

则

$$
1+x_n>1>0,
$$

从而

$$
x_{n+1}=\frac{1}{1+x_n}>0.
$$

由数学归纳法，所有正整数 $n$ 都满足

$$
x_n>0.
$$

**本步结论**：数列恒为正，递推式始终有意义。

### 第二步：判断每一项在候选极限的哪一侧

**本步目标**：解释震荡的结构，并为奇偶子列的界作准备。

**执行分析**：候选极限 $\alpha$ 是递推函数的不动点，因此把 $x_{n+1}$ 与 $\alpha$ 作差时，可以利用

$$
\alpha=\frac{1}{1+\alpha}.
$$

**详细推导**：

$$
\begin{aligned}
x_{n+1}-\alpha
&=\frac{1}{1+x_n}-\frac{1}{1+\alpha}\\
&=\frac{1+\alpha-(1+x_n)}{(1+x_n)(1+\alpha)}\\
&=\frac{\alpha-x_n}{(1+x_n)(1+\alpha)}\\
&=-\frac{x_n-\alpha}{(1+x_n)(1+\alpha)}.
\end{aligned}
$$

由第一步，分母满足

$$
(1+x_n)(1+\alpha)>0.
$$

所以 $x_{n+1}-\alpha$ 与 $x_n-\alpha$ 符号相反。

又因为

$$
x_1=1>\alpha,
$$

所以

$$
x_2<\alpha,quad x_3>\alpha,quad x_4<\alpha,quad\ldots
$$

即对所有正整数 $k$，

$$
x_{2k-1}>\alpha,qquad x_{2k}<\alpha.
$$

**本步结论**：奇数项始终在 $\alpha$ 上方，偶数项始终在 $\alpha$ 下方；原数列的震荡来自递推函数每次都把不等号方向翻转。

### 第三步：写出二步递推式

**本步目标**：消去一次迭代造成的方向反转，使单调性能够被直接比较。

**执行分析**：把递推式再迭代一次，让 $x_{n+2}$ 直接表示成 $x_n$ 的函数。

**详细推导**：

$$
\begin{aligned}
x_{n+2}
&=\frac{1}{1+x_{n+1}}\\
&=\frac{1}{1+\frac{1}{1+x_n}}\\
&=\frac{1}{\frac{1+x_n+1}{1+x_n}}\\
&=\frac{1+x_n}{2+x_n}.
\end{aligned}
$$

因此

$$
x_{n+2}=\frac{1+x_n}{2+x_n}.
$$

**本步结论**：相隔两项的数满足同一个二步递推关系，可以分别研究奇数子列和偶数子列。

### 第四步：证明奇数子列递减、偶数子列递增

**本步目标**：为两条子列应用单调有界定理准备单调性条件。

**执行分析**：直接比较 $x_{n+2}$ 与 $x_n$。作差后，符号应当与 $x_n$ 位于 $\alpha$ 的哪一侧有关。

**详细推导**：

$$
\begin{aligned}
x_{n+2}-x_n
&=\frac{1+x_n}{2+x_n}-x_n\\
&=\frac{1+x_n-x_n(2+x_n)}{2+x_n}\\
&=\frac{1+x_n-2x_n-x_n^2}{2+x_n}\\
&=\frac{1-x_n-x_n^2}{2+x_n}\\
&=-\frac{x_n^2+x_n-1}{2+x_n}.
\end{aligned}
$$

由于 $\alpha$ 满足

$$
\alpha^2+\alpha-1=0,
$$

另一个根为

$$
-1-\alpha.
$$

所以

$$
x_n^2+x_n-1=(x_n-\alpha)(x_n+1+\alpha).
$$

代回作差式：

$$
x_{n+2}-x_n
=-rac{(x_n-\alpha)(x_n+1+\alpha)}{2+x_n}.
$$

由 $x_n>0$ 和 $\alpha>0$，有

$$
x_n+1+\alpha>0,qquad 2+x_n>0.
$$

因此 $x_{n+2}-x_n$ 的符号与 $x_n-\alpha$ 的符号相反。

当 $n=2k-1$ 时，第二步已经证明

$$
x_{2k-1}>\alpha.
$$

于是

$$
x_{2k+1}-x_{2k-1}<0,
$$

即

$$
x_{2k+1}<x_{2k-1}.
$$

所以奇数子列严格递减。

当 $n=2k$ 时，第二步已经证明

$$
x_{2k}<\alpha.
$$

于是

$$
x_{2k+2}-x_{2k}>0,
$$

即

$$
x_{2k+2}>x_{2k}.
$$

所以偶数子列严格递增。

**本步结论**：奇数子列递减且始终大于 $\alpha$；偶数子列递增且始终小于 $\alpha$。

### 第五步：证明两条子列收敛

**本步目标**：严谨建立极限存在性，补上不动点法留下的逻辑缺口。

**执行分析**：第四步给出了单调性，第二步给出了界，因此现在才具备使用单调有界定理的全部条件。

**详细推导**：奇数子列满足

$$
x_{2k-1}>\alpha
$$

且严格递减，所以它单调递减并且有下界 $\alpha$。由单调有界定理，存在实数 $A$，使得

$$
\lim_{k\to\infty}x_{2k-1}=A.
$$

偶数子列满足

$$
x_{2k}<\alpha
$$

且严格递增，所以它单调递增并且有上界 $\alpha$。由单调有界定理，存在实数 $B$，使得

$$
\lim_{k\to\infty}x_{2k}=B.
$$

**本步结论**：奇数子列和偶数子列都存在极限。

### 第六步：求两条子列的极限并回到原数列

**本步目标**：证明两条子列趋于同一点，从而证明整个数列收敛。

**执行分析**：现在极限已经存在，可以合法地对二步递推式取极限。二步递推同时适用于奇数项和偶数项。

**详细推导**：对奇数子列使用二步递推式

$$
x_{2k+1}=\frac{1+x_{2k-1}}{2+x_{2k-1}}.
$$

令 $k$ 趋于无穷，得到

$$
A=\frac{1+A}{2+A}.
$$

因为 $A>0$，所以 $2+A>0$。两边乘以 $2+A$：

$$
A(2+A)=1+A.
$$

展开并整理：

$$
A^2+2A=1+A,
$$

$$
A^2+A-1=0.
$$

正根唯一，因此

$$
A=\alpha=\frac{\sqrt5-1}{2}.
$$

同理，对偶数子列使用

$$
x_{2k+2}=\frac{1+x_{2k}}{2+x_{2k}},
$$

可得

$$
B=\frac{1+B}{2+B},
$$

从而

$$
B^2+B-1=0.
$$

由于 $B>0$，所以

$$
B=\alpha=\frac{\sqrt5-1}{2}.
$$

于是

$$
\lim_{k\to\infty}x_{2k-1}
=\lim_{k\to\infty}x_{2k}
=\frac{\sqrt5-1}{2}.
$$

任意足够靠后的数列项不是奇数项就是偶数项，而两类项都趋于同一个极限，因此原数列也趋于该值。

**本步结论**：

$$
\boxed{\lim_{n\to\infty}x_n=\frac{\sqrt5-1}{2}}.
$$

## What this example should teach the skill

- A fixed-point calculation produces a candidate only; it does not establish convergence.
- Testing the first few terms is a legitimate heuristic check and can reveal that a proposed monotonicity route fails for the full sequence.
- A decreasing one-step map suggests alternating behavior; two iterations or parity subsequences may expose hidden monotonicity.
- The formal solution must prove positivity, side-of-fixed-point behavior, monotonicity, boundedness, and equality of subsequential limits in the order required by the logic.
- Phrases such as “同理” should not hide a substantive limit argument; the parallel calculation may be shorter, but its equation and conclusion should still be visible.
