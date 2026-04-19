# 物體在空氣中下落的速度變化建模

當物體在空氣中下落時，其運動受到重力與空氣阻力的共同作用。以下透過牛頓第二定律建立微分方程並求解。

## 1. 物理建模 (Newton's Second Law)

根據牛頓第二定律 $F = ma$，定義向下為正方向：
* **重力**： $F_g = mg$
* **空氣阻力**（線性阻力模型）：$F_d = cv$ (其中 $c$ 為阻力係數)

運動方程式為：
$$m \frac{dv}{dt} = mg - cv$$

---

## 2. 推導過程

### Step 1：分離變數 (Separation of Variables)
我們的目標是將含有速度 $v$ 的項移到方程式一邊，含有時間 $t$ 的項移到另一邊。將方程式兩邊同除以 $(mg - cv)$，並同乘 $dt/m$：
$$\frac{dv}{mg - cv} = \frac{dt}{m}$$

### Step 2：兩邊同時積分 (Integration)
對方程式兩邊分別進行積分：
$$\int \frac{1}{mg - cv} \, dv = \int \frac{1}{m} \, dt$$

**處理左邊積分**（使用代換積分法）：
令 $u = mg - cv$，則 $du = -c \, dv \implies dv = -\frac{1}{c} \, du$。
代入得：
$$-\frac{1}{c} \int \frac{1}{u} \, du = -\frac{1}{c} \ln|mg - cv|$$

**處理右邊積分**：
$$\int \frac{1}{m} \, dt = \frac{t}{m} + C_1$$

合併兩邊：
$$-\frac{1}{c} \ln|mg - cv| = \frac{t}{m} + C_1$$

### Step 3：化簡並求解 $v(t)$
兩邊同乘 $-c$：
$$\ln|mg - cv| = -\frac{c}{m}t - cC_1$$

取指數函數 $e$ 消除對數：
$$mg - cv = e^{-\frac{c}{m}t - cC_1} = e^{-cC_1} \cdot e^{-\frac{c}{m}t}$$

令常數 $K = \pm e^{-cC_1}$：
$$mg - cv = K e^{-\frac{c}{m}t}$$
$$cv = mg - K e^{-\frac{c}{m}t}$$
$$v(t) = \frac{mg}{c} - \frac{K}{c} e^{-\frac{c}{m}t}$$

令新常數 $A = -\frac{K}{c}$，得到一般解：
$$v(t) = \frac{mg}{c} + A e^{-\frac{c}{m}t}$$

### Step 4：代入初始條件 (Initial Condition)
假設物體由靜止釋放，即 $t=0$ 時，$v=0$：
$$0 = \frac{mg}{c} + A e^0 \implies A = -\frac{mg}{c}$$

---

## 3. 最終結果 (Final Solution)

將 $A$ 代回一般解，並提取公因式 $\frac{mg}{c}$：

$$v(t) = \frac{mg}{c} \left( 1 - e^{-\frac{ct}{m}} \right)$$

---

## 4. 物理意義討論

1.  **終端速度 (Terminal Velocity)**：
    當 $t \to \infty$ 時， $e^{-\frac{ct}{m}} \to 0$ ，速度趨近於穩定值：
    $$v_{terminal} = \frac{mg}{c}$$
    此時重力與阻力平衡，加速度為零。

2.  **速度變化趨勢**：
    物體的速度隨時間呈指數級增加，但增加的速率（加速度）逐漸減小，最終無限趨近於終端速度。
