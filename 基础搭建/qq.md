# 🎲 赌徒破产问题（Gambler's Ruin）公式

## 1. A最终破产B的概率（A获胜概率）

### 通用公式：
\[
P_a = 
\begin{cases} 
\dfrac{1 - \left(\dfrac{q}{p}\right)^a}{1 - \left(\dfrac{q}{p}\right)^{a+b}} & \text{若 } p \neq q \\
\\
\dfrac{a}{a+b} & \text{若 } p = q = 0.5 
\end{cases}
\]

### 赌场无限资金情况（b → ∞）：
\[
P_a = 
\begin{cases} 
1 - \left(\dfrac{q}{p}\right)^a & \text{若 } p > q \\
0 & \text{若 } p \leq q
\end{cases}