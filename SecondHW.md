# 用拉普拉斯解二階微分方程

題目：

$$
2x''+7x'+3x=0
$$

初始條件：

$$
x(0)=0,\quad x'(0)=1
$$

---

## 1. 設拉普拉斯轉換

令：

$$
\mathcal{L}\{x(t)\}=X(s)
$$

拉普拉斯公式：

$$
\mathcal{L}\{x'\}=sX(s)-x(0)
$$

$$
\mathcal{L}\{x''\}=s^2X(s)-sx(0)-x'(0)
$$

代入初始條件：

$$
x(0)=0,\quad x'(0)=1
$$

所以：

$$
\mathcal{L}\{x'\}=sX(s)
$$

$$
\mathcal{L}\{x''\}=s^2X(s)-1
$$

---

## 2. 對原方程取拉普拉斯

原方程為：

$$
2x''+7x'+3x=0
$$

兩邊取拉普拉斯：

$$
\mathcal{L}\{2x''+7x'+3x\}=\mathcal{L}\{0\}
$$

因此：

$$
2\mathcal{L}\{x''\}+7\mathcal{L}\{x'\}+3\mathcal{L}\{x\}=0
$$

代入前面結果：

$$
2(s^2X(s)-1)+7sX(s)+3X(s)=0
$$

展開：

$$
2s^2X(s)-2+7sX(s)+3X(s)=0
$$

將 $X(s)$ 提出：

$$
(2s^2+7s+3)X(s)-2=0
$$

所以：

$$
(2s^2+7s+3)X(s)=2
$$

得到：

$$
X(s)=\frac{2}{2s^2+7s+3}
$$

---

## 3. 分解分母

分母可分解為：

$$
2s^2+7s+3=(2s+1)(s+3)
$$

所以：

$$
X(s)=\frac{2}{(2s+1)(s+3)}
$$

因為：

$$
2s+1=2\left(s+\frac12\right)
$$

所以：

$$
X(s)=\frac{2}{2\left(s+\frac12\right)(s+3)}
$$

化簡得：

$$
X(s)=\frac{1}{\left(s+\frac12\right)(s+3)}
$$

---

## 4. 部分分式分解

設：

$$
\frac{1}{\left(s+\frac12\right)(s+3)}
=
\frac{A}{s+\frac12}+\frac{B}{s+3}
$$

兩邊同乘分母：

$$
1=A(s+3)+B\left(s+\frac12\right)
$$

令：

$$
s=-\frac12
$$

則：

$$
1=A\left(-\frac12+3\right)
$$

$$
1=A\left(\frac52\right)
$$

所以：

$$
A=\frac25
$$

再令：

$$
s=-3
$$

則：

$$
1=B\left(-3+\frac12\right)
$$

$$
1=B\left(-\frac52\right)
$$

所以：

$$
B=-\frac25
$$

因此：

$$
X(s)=\frac{\frac25}{s+\frac12}-\frac{\frac25}{s+3}
$$

---

## 5. 反拉普拉斯

使用公式：

$$
\mathcal{L}^{-1}\left\{\frac{1}{s+a}\right\}=e^{-at}
$$

所以：

$$
\mathcal{L}^{-1}\left\{\frac{1}{s+\frac12}\right\}=e^{-\frac12t}
$$

$$
\mathcal{L}^{-1}\left\{\frac{1}{s+3}\right\}=e^{-3t}
$$

因此：

$$
x(t)=\frac25e^{-\frac12t}-\frac25e^{-3t}
$$

---

## 最終答案

$$
\boxed{x(t)=\frac25\left(e^{-\frac12t}-e^{-3t}\right)}
$$
