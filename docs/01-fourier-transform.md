# 第一章 傅里叶变换

## 一、傅里叶级数

设 $f(x)$ 是定义在 $[-l,l]$ 上的、以 $2l$ 为周期的函数，并满足 Dirichlet 条件：

1. 在一个周期内连续，或至多有有限个第一类间断点；
2. 在一个周期内至多有有限个极值点。

则其傅里叶级数写为

$$
f(x)\sim\frac{a_0}{2}+\sum_{k=1}^{\infty}\left(a_k\cos\frac{k\pi x}{l}+b_k\sin\frac{k\pi x}{l}\right).
$$

在连续点处，级数收敛于 $f(x)$；在间断点处，级数收敛于左右极限的平均值：

$$
\frac{1}{2}\bigl[f(x-0)+f(x+0)\bigr].
$$

### 1. 三角函数系的正交性

由欧拉公式 $2\cos\theta=e^{i\theta}+e^{-i\theta}$，可得

$$
\cos(\alpha+\beta)=\cos\alpha\cos\beta-\sin\alpha\sin\beta,
\qquad
\sin(\alpha+\beta)=\sin\alpha\cos\beta+\cos\alpha\sin\beta.
$$

对于正整数 $k,m$，在 $[-l,l]$ 上有

$$
\int_{-l}^{l}\cos\frac{k\pi x}{l}\cos\frac{m\pi x}{l}\,dx
=\begin{cases}0,&k\ne m,\\l,&k=m,\end{cases}
$$

$$
\int_{-l}^{l}\sin\frac{k\pi x}{l}\sin\frac{m\pi x}{l}\,dx
=\begin{cases}0,&k\ne m,\\l,&k=m,\end{cases}
$$

$$
\int_{-l}^{l}\sin\frac{k\pi x}{l}\cos\frac{m\pi x}{l}\,dx=0,
\qquad
\int_{-l}^{l}\cos\frac{k\pi x}{l}\,dx
=\int_{-l}^{l}\sin\frac{k\pi x}{l}\,dx=0.
$$

例如，利用积化和差公式

$$
2\cos\alpha\cos\beta=\cos(\alpha+\beta)+\cos(\alpha-\beta),
$$

当 $k\ne m$ 时，余弦与余弦的乘积在 $[-l,l]$ 上的积分为零；当 $k=m$ 时，利用 $2\cos^2\alpha=1+\cos 2\alpha$，积分等于 $l$。同理可得其余正交关系。

> **附注：**板书中用于推导正弦与余弦正交性的积化和差式，右侧写作两个余弦之差；该式对应的是 $2\sin\alpha\sin\beta$。正弦与余弦的乘积也可直接利用奇偶性得到积分为零。板书末尾关于完备性的等式右侧仍含 $x$，不能直接与左侧的定积分相等，因此这里保留上述正交关系，不将该式作为结论使用。

### 2. 傅里叶系数

将级数两边从 $-l$ 到 $l$ 积分，由正交性得

$$
\int_{-l}^{l}f(x)\,dx=a_0l,
\qquad
a_0=\frac{1}{l}\int_{-l}^{l}f(x)\,dx.
$$

两边同乘 $\cos(k\pi x/l)$ 并积分，对于 $k\geq1$，得

$$
\int_{-l}^{l}f(x)\cos\frac{k\pi x}{l}\,dx
=a_k\int_{-l}^{l}\cos^2\frac{k\pi x}{l}\,dx=la_k,
$$

因此

$$
a_k=\frac{1}{l}\int_{-l}^{l}f(x)\cos\frac{k\pi x}{l}\,dx,
\qquad
b_k=\frac{1}{l}\int_{-l}^{l}f(x)\sin\frac{k\pi x}{l}\,dx.
$$

若 $f(x)$ 为奇函数，则其级数只含正弦项；若 $f(x)$ 为偶函数，则其级数只含常数项和余弦项：

$$
f(x)\sim\sum_{k=1}^{\infty}b_k\sin\frac{k\pi x}{l}
\quad(\text{奇函数}),
\qquad
f(x)\sim\frac{a_0}{2}+\sum_{k=1}^{\infty}a_k\cos\frac{k\pi x}{l}
\quad(\text{偶函数}).
$$

### 3. 复指数形式

由

$$
\cos\theta=\frac{e^{i\theta}+e^{-i\theta}}{2},\qquad
\sin\theta=\frac{e^{i\theta}-e^{-i\theta}}{2i},
$$

傅里叶级数可写为

$$
f(x)\sim\sum_{k=-\infty}^{\infty}C_k e^{i\omega_kx},
\qquad \omega_k=\frac{k\pi}{l},\quad k=0,\pm1,\pm2,\ldots,
$$

其中

$$
C_k=\frac{1}{2l}\int_{-l}^{l}f(x)e^{-i\omega_kx}\,dx.
$$

对于实值函数，当 $k\geq1$ 时，

$$
C_k=\frac{a_k-ib_k}{2},\qquad C_{-k}=\overline{C_k},\qquad C_0=\frac{a_0}{2}.
$$

## 二、傅里叶积分

当周期 $2l$ 趋于无穷，满足适当条件的函数可表示为傅里叶积分：

$$
f(x)=\int_0^\infty A(\omega)\cos\omega x\,d\omega
+\int_0^\infty B(\omega)\sin\omega x\,d\omega,
$$

其中

$$
A(\omega)=\frac{1}{\pi}\int_{-\infty}^{\infty}f(t)\cos\omega t\,dt,
\qquad
B(\omega)=\frac{1}{\pi}\int_{-\infty}^{\infty}f(t)\sin\omega t\,dt.
$$

在间断点，积分表示的值取左右极限的平均值。

> **附注：**板书中将 $\int_{-\infty}^{\infty}|f(x)|\,dx<\infty$ 推至 $\lim_{x\to\pm\infty}f(x)=0$。绝对可积本身不足以保证该极限成立；需要另外的条件。绝对可积可以保证傅里叶系数中的常数项 $a_0$ 在 $l\to\infty$ 时趋于零。

若 $f$ 是偶函数，则正弦项消失，得到余弦积分表示：

$$
f(x)=\int_0^\infty A(\omega)\cos\omega x\,d\omega,
\qquad
A(\omega)=\frac{2}{\pi}\int_0^\infty f(t)\cos\omega t\,dt.
$$

对奇函数，可采用对称归一化的正弦变换形式：

$$
f(x)=\sqrt{\frac{2}{\pi}}\int_0^\infty B(\omega)\sin\omega x\,d\omega,
\qquad
B(\omega)=\sqrt{\frac{2}{\pi}}\int_0^\infty f(t)\sin\omega t\,dt.
$$

### 例：矩形函数

定义

$$
\operatorname{rect}(x)=\begin{cases}
1,&|x|\leq\frac12,\\
0,&|x|>\frac12.
\end{cases}
$$

设 $T>0$，令

$$
f(x)=h\operatorname{rect}\left(\frac{x}{2T}\right)
=\begin{cases}h,&|x|\leq T,\\0,&|x|>T.\end{cases}
$$

由于 $f$ 是偶函数，由余弦积分公式得到

$$
\begin{aligned}
A(\omega)
&=\frac{2}{\pi}\int_0^\infty h\operatorname{rect}\left(\frac{x}{2T}\right)\cos\omega x\,dx\\
&=\frac{2h}{\pi}\int_0^T\cos\omega x\,dx
=\frac{2h}{\pi}\frac{\sin\omega T}{\omega}.
\end{aligned}
$$

其中 $A(0)$ 按极限取值 $2hT/\pi$。因此

$$
f(x)=\frac{2h}{\pi}\int_0^\infty\frac{\sin\omega T}{\omega}\cos\omega x\,d\omega,
$$

在 $x=\pm T$ 处，右侧取值为 $h/2$。

## 三、复数形式的傅里叶积分与傅里叶变换

由欧拉公式，傅里叶积分可以改写为

$$
\begin{aligned}
f(x)={}&\frac12\int_0^\infty[A(\omega)-iB(\omega)]e^{i\omega x}\,d\omega\\
&+\frac12\int_0^\infty[A(\omega)+iB(\omega)]e^{-i\omega x}\,d\omega.
\end{aligned}
$$

将第二项中的频率换元为负频率，得到复数形式的傅里叶积分

$$
f(x)=\int_{-\infty}^{\infty}F(\omega)e^{i\omega x}\,d\omega,
\qquad
F(\omega)=\frac1{2\pi}\int_{-\infty}^{\infty}f(x)e^{-i\omega x}\,dx.
$$

其中，对于 $\omega>0$，$F(\omega)=\tfrac12[A(\omega)-iB(\omega)]$；对于 $\omega<0$，$F(\omega)=\tfrac12[A(-\omega)+iB(-\omega)]$。

以下记 $F(\omega)=\mathcal F[f](\omega)$，上面两式分别为正变换与逆变换。其他常见的归一化方式也可采用，但一对正、逆变换的系数必须配套。

> **附注：**板书在复数形式下还出现了 $1/\sqrt{2\pi}$ 的系数；它属于对称归一化的一种写法。后续微分等公式使用的正变换系数为 $1/(2\pi)$，故此处列出与后续公式一致的一对变换。

## 四、傅里叶变换的性质

以下各式在相应积分、换元与分部积分成立的条件下使用，仍采用上述变换约定。

### 1. 微分与积分

若 $f(x)\to0$（$x\to\pm\infty$），对导数的变换分部积分，得

$$
\begin{aligned}
\mathcal F[f'](\omega)
&=\frac1{2\pi}\int_{-\infty}^{\infty}f'(x)e^{-i\omega x}\,dx\\
&=\frac1{2\pi}\left[f(x)e^{-i\omega x}\right]_{-\infty}^{\infty}
+\frac{i\omega}{2\pi}\int_{-\infty}^{\infty}f(x)e^{-i\omega x}\,dx\\
&=i\omega F(\omega).
\end{aligned}
$$

类似地，

$$
\mathcal F[f^{(n)}](\omega)=(i\omega)^nF(\omega).
$$

若 $g(x)=\int_{-\infty}^{x}f(t)\,dt$ 且 $g$ 满足上述微分公式的条件，则对 $\omega\ne0$，

$$
\mathcal F[g](\omega)=\frac{F(\omega)}{i\omega}.
$$

相应地，满足条件的 $n$ 重积分对应因子 $(i\omega)^{-n}$。

> **附注：**积分公式在 $\omega=0$ 处需要特别处理；若原函数不趋于零，还可能出现与 $\delta(\omega)$ 有关的项，见后面的阶跃函数例子。

### 2. 缩放、平移与频移

$$
\mathcal F[f(ax)](\omega)=\frac1{|a|}F\left(\frac{\omega}{a}\right),\qquad a\ne0;
$$

$$
\mathcal F[f(x-x_0)](\omega)=e^{-i\omega x_0}F(\omega),
\qquad
\mathcal F[e^{i\omega_0x}f(x)](\omega)=F(\omega-\omega_0).
$$

> **附注：**板书缩放公式中的系数写为 $1/a$；当 $a>0$ 时与上式一致。若允许 $a<0$，换元时还需考虑积分上下限的交换，系数应为 $1/|a|$。

### 3. 卷积

定义函数 $f_1,f_2$ 的卷积为

$$
(f_1*f_2)(x)=\int_{-\infty}^{\infty}f_1(t)f_2(x-t)\,dt
=(f_2*f_1)(x).
$$

设 $F_1=\mathcal F[f_1]$，$F_2=\mathcal F[f_2]$。由定义并交换积分次序，

$$
\begin{aligned}
\mathcal F[f_1*f_2](\omega)
&=\frac1{2\pi}\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}
f_1(t)f_2(x-t)e^{-i\omega x}\,dt\,dx\\
&=2\pi F_1(\omega)F_2(\omega).
\end{aligned}
$$

## 五、Dirac $\delta$ 函数

### 1. 定义与基本性质

直观地，$\delta(x)$ 在 $x\ne0$ 时为零，在原点集中，并满足

$$
\int_{-\infty}^{\infty}\delta(x)\,dx=1.
$$

当 $a<b$ 且端点均不为零时，

$$
\int_a^b\delta(x)\,dx=\begin{cases}0,&ab>0,\\1,&ab<0.\end{cases}
\qquad
\int_{-\varepsilon}^{\varepsilon}\delta(x)\,dx=1\quad(\varepsilon>0).
$$

其筛选性质为

$$
\int_{-\infty}^{\infty}f(x)\delta(x-x_0)\,dx=f(x_0),
$$

其中 $f$ 在 $x_0$ 处连续。若 $\varphi(x)$ 的零点 $x_k$ 均为单根，即 $\varphi'(x_k)\ne0$，则

$$
\delta(\varphi(x))=\sum_k\frac{\delta(x-x_k)}{|\varphi'(x_k)|}.
$$

> **附注：**$\delta$ 不是通常意义下由各点函数值确定的普通函数；“原点处无穷大”的说法是对集中性质的直观描述。上述等式在广义函数意义下理解。

### 2. 阶跃函数与 $\delta$ 函数

取阶跃函数

$$
H(x)=\begin{cases}0,&x\leq0,\\1,&x>0.\end{cases}
$$

在广义函数意义下，

$$
H(x)=\int_{-\infty}^{x}\delta(t)\,dt,
\qquad \delta(x)=H'(x),\qquad \delta(-x)=\delta(x).
$$

$H(0)$ 的单点取值不改变它所定义的广义函数。

将 $\delta(x)$ 代入上述傅里叶变换，得到

$$
\mathcal F[\delta](\omega)=\frac1{2\pi},
\qquad
\delta(x)=\frac1{2\pi}\int_{-\infty}^{\infty}e^{i\omega x}\,d\omega.
$$

后一个积分表示按广义函数意义理解。

### 3. 阶跃函数的傅里叶变换

由于 $H$ 的积分在正半轴发散，引入 $\varepsilon>0$，令

$$
H(x,\varepsilon)=\begin{cases}e^{-\varepsilon x},&x>0,\\0,&x\leq0.\end{cases}
\qquad H(x)=\lim_{\varepsilon\to0^+}H(x,\varepsilon).
$$

则

$$
\mathcal F[H(x,\varepsilon)](\omega)
=\frac1{2\pi}\int_0^\infty e^{-(\varepsilon+i\omega)x}\,dx
=\frac1{2\pi}\frac1{\varepsilon+i\omega}.
$$

取广义函数极限，得

$$
\mathcal F[H](\omega)=\frac12\delta(\omega)
-\frac{i}{2\pi}\operatorname{PV}\frac1\omega,
$$

其中 $\operatorname{PV}$ 表示 Cauchy 主值。

### 4. 三维 $\delta$ 函数

对 $\mathbf r=(x,y,z)$，三维 $\delta$ 函数可表示为

$$
\delta(\mathbf r)=\delta(x)\delta(y)\delta(z).
$$