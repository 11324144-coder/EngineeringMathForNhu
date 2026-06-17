# 方波信號分析與 RLC 電路頻率響應

## 一、100 MHz 時鐘方波的傅立葉級數

已知：

$$
T = 10\text{ ns},\quad f_0 = \frac{1}{T} = 100\text{ MHz}
$$

$$ V_{OH}=3.3V,\quad V_{OL}=0V $$

占空比為 50%，所以平均值為：

$$
V_{DC}=\frac{3.3+0}{2}=1.65V
$$

50% 占空比方波只含有奇次諧波，因此可展開為：

$$
v(t)=1.65+\frac{6.6}{\pi}
\left[
\sin(\omega_0 t)
+\frac{1}{3}\sin(3\omega_0 t)
+\frac{1}{5}\sin(5\omega_0 t)
+\cdots
\right]
$$

其中：

$$
\omega_0=2\pi f_0=2\pi(100\text{ MHz})
$$

也就是：

$$
v(t)=1.65+\frac{6.6}{\pi}
\left[
\sin(2\pi\cdot100\text{ MHz}\cdot t)
+\frac{1}{3}\sin(2\pi\cdot300\text{ MHz}\cdot t)
+\frac{1}{5}\sin(2\pi\cdot500\text{ MHz}\cdot t)
+\cdots
\right]
$$

頻率成分如下：

| 成分    |      頻率 |       振幅 |
| ----- | ------: | -------: |
| DC    |    0 Hz |   1.65 V |
| 基波    | 100 MHz | 約 2.10 V |
| 3 次諧波 | 300 MHz | 約 0.70 V |
| 5 次諧波 | 500 MHz | 約 0.42 V |
| 7 次諧波 | 700 MHz | 約 0.30 V |

一般式為：

$$
A_n=\frac{6.6}{n\pi},\quad n=1,3,5,\cdots
$$

---

## 二、為什麼長導線會讓方波邊沿變緩？

理想方波需要很多高頻諧波疊加，尤其是 3、5、7、9 次以上的高頻成分，才能形成很陡的上升沿與下降沿。

長導線傳輸時會有寄生效應，例如：

$$
R_{wire},\quad L_{wire},\quad C_{wire}
$$

這些寄生電阻、電感與電容會讓導線表現得像一個低通濾波器。高頻諧波比低頻基波更容易被衰減，因此原本方波中的高頻成分會消失。

結果是：

$$
\text{高頻諧波減少}
\Rightarrow
\text{邊沿不再銳利}
\Rightarrow
\text{上升時間、下降時間變長}
$$

所以經過長導線後，方波會變得比較圓滑，接近被濾波後的波形。

---

## 三、RLC 電路頻率響應分析

題目給：

$$
R=10\Omega
$$

$$
L=1\text{ mH}=10^{-3}H
$$

$$
C=2.53\times10^{-8}F
$$

輸入訊號為 50% 占空比矩形波：

$$
v_i(t)=
\begin{cases}
V_m, & 0<t<T/2 \
0, & T/2<t<T
\end{cases}
$$

其中：

$$
V_m=5V,\quad f_0=1\text{ MHz},\quad T=1\mu s
$$

---

## 四、輸入訊號傅立葉展開

50% 占空比的單極性矩形波可寫成：

$$
v_i(t)=\frac{V_m}{2}
+
\frac{2V_m}{\pi}
\left[
\sin(\omega_0 t)
+\frac{1}{3}\sin(3\omega_0 t)
+\frac{1}{5}\sin(5\omega_0 t)
+\cdots
\right]
$$

因為題目只考慮 DC、基波與 3 次諧波，所以取：

$$
v_i(t)\approx
2.5
+
\frac{10}{\pi}\sin(2\pi\cdot1\text{ MHz}\cdot t)
+
\frac{10}{3\pi}\sin(2\pi\cdot3\text{ MHz}\cdot t)
$$

也就是：

$$
v_i(t)\approx
2.5
+
3.183\sin(2\pi\cdot1\text{ MHz}\cdot t)
+
1.061\sin(2\pi\cdot3\text{ MHz}\cdot t)
$$

---

## 五、輸出取電容兩端電壓的轉移函數

串聯 RLC 中，若輸出取電容兩端：

$$
H(j\omega)=\frac{V_C}{V_i}
==========================

\frac{Z_C}{R+j\omega L+Z_C}
$$

其中：

$$
Z_C=\frac{1}{j\omega C}
$$

整理後：

$$
H(j\omega)=
\frac{1}{1-\omega^2LC+j\omega RC}
$$

其大小為：

$$
|H(j\omega)|=
\frac{1}{
\sqrt{(1-\omega^2LC)^2+(\omega RC)^2}
}
$$

相位為：

$$
\angle H(j\omega)
=================

-\tan^{-1}
\left(
\frac{\omega RC}{1-\omega^2LC}
\right)
$$

---

## 六、諧振頻率

RLC 諧振頻率為：

$$
f_r=
\frac{1}{2\pi\sqrt{LC}}
$$

代入：

$$
f_r=
\frac{1}{2\pi\sqrt{(10^{-3})(2.53\times10^{-8})}}
$$

$$
f_r\approx31.6\text{ kHz}
$$

所以這組 RLC 的諧振頻率約為：

$$
\boxed{31.6\text{ kHz}}
$$

這裡要注意：題目輸入的基波是 1 MHz，但電路諧振頻率只有 31.6 kHz，兩者差很多，因此 1 MHz 和 3 MHz 都會被明顯衰減。

---

## 七、計算 DC、1 MHz、3 MHz 輸出

### 1. DC 成分

當：

$$
\omega=0
$$

則：

$$
H(0)=1
$$

所以 DC 輸出為：

$$
V_{o,DC}=2.5V
$$

---

### 2. 基波 1 MHz

$$
f=1\text{ MHz}
$$

計算得到：

$$
|H(j\omega_0)|\approx0.001002
$$

輸入基波振幅為：

$$
A_1=\frac{10}{\pi}\approx3.183V
$$

所以輸出基波振幅：

$$
A_{1,out}=3.183\times0.001002
$$

$$
A_{1,out}\approx0.00319V
$$

$$
\boxed{A_{1,out}\approx3.19mV}
$$

相位約為：

$$
\angle H(j\omega_0)\approx -179.9^\circ
$$

---

### 3. 三次諧波 3 MHz

$$
f=3\text{ MHz}
$$

計算得到：

$$
|H(j3\omega_0)|\approx0.000111
$$

輸入三次諧波振幅為：

$$
A_3=\frac{10}{3\pi}\approx1.061V
$$

所以輸出三次諧波振幅：

$$
A_{3,out}=1.061\times0.000111
$$

$$
A_{3,out}\approx0.000118V
$$

$$
\boxed{A_{3,out}\approx0.118mV}
$$

相位約為：

$$
\angle H(j3\omega_0)\approx -180^\circ
$$

---

## 八、輸出波形近似式

因此輸出可寫成：

$$
v_o(t)\approx
2.5
+
0.00319\sin(2\pi\cdot1\text{ MHz}\cdot t-179.9^\circ)
+
0.000118\sin(2\pi\cdot3\text{ MHz}\cdot t-180^\circ)
$$

也就是輸出幾乎只剩下 DC 分量：

$$
\boxed{v_o(t)\approx2.5V}
$$

1 MHz 和 3 MHz 的交流成分都被嚴重衰減。

---

## 九、結論

方波可以看成 DC、基波與多個奇次諧波的疊加。數位時鐘訊號的邊沿越陡，代表其中包含越多高頻諧波。當方波經過長導線或具有寄生 RLC 的傳輸路徑時，高頻諧波會被衰減，因此上升沿與下降沿會變慢，波形會變得圓滑。

在 RLC 電路部分，依照題目給的數值：

$$
R=10\Omega,\quad L=1\text{ mH},\quad C=2.53\times10^{-8}F
$$

其諧振頻率為：

$$
f_r\approx31.6\text{ kHz}
$$

但輸入基波為：

$$
f_0=1\text{ MHz}
$$

因此 1 MHz 與 3 MHz 都遠高於諧振頻率，輸出取電容兩端時，這些高頻成分會被大幅衰減。最後輸出主要保留 DC 分量，基波與三次諧波只剩下很小的 mV 等級訊號。
