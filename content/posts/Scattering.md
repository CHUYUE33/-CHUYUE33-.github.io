+++
title = 'Scattering'
date = 2024-04-14T15:38:00-07:00
draft = true
tags = ['scattering']
series = ['QuantumMechanics II']
categories = ['Physics']
+++
#QuantumMechanics 

## 经典散射理论
一个以能量$E$，距离散射中心轴$b$，以偏转角$\theta$出射的粒子，这是常见的散射模型。我们需要确定$b$和$\theta$之间的关系。
总的来说，散射截面$d\sigma$内的入射粒子都会散射到一个立体角微元$d\Omega$，这两个成正比，我们定义微分散射截面
$$d\sigma=D(\theta)d\Omega\tag{1}$$
带入impact parameter$b$和方位角$\phi$，$d\sigma=b \ db d\phi$，$d\Omega=\sin\theta d\theta d\phi$，所以
$$D(\theta)=\frac{b}{\sin\theta}| \frac{db}{d\theta}|\tag{2}$$
那么总的散射截面可以写作对于$D(\theta)$全部立体角的积分：
$$\sigma \equiv \int D(\theta) \, d\Omega\tag{3} $$

对于入射的粒子束，我们定义$\mathscr{L}\equiv \text{number of incident particles per unit area,per unit time}$，那么单位时间进入散射截面$d\sigma$的粒子数为$dN=\mathscr{L}d\sigma=\mathscr{L}d\Omega$
所以$$D(\theta)=\frac{1}{\mathscr{L}} \frac{dN}{d\Omega}\tag{4}$$

## 量子散射理论
我们想象沿着z方向入射的的平面波$\psi(z)=Ae^{ikz}$，遇到了一个球形的散射势能场，那么现在的整体波函数通解应写作
$$\boxed{\psi(r,\theta)\approx A\left\{ e^{ikz}+f(\theta,\phi) \frac{e^{ikr}}{r} \right\},\quad \text{for large r}}\tag{5}$$
式子中第一项代表原本的入射平面波，第二项为散射球面波表达式，$\frac{1}{r}$因子是为了让概率积分收敛，入射波波数定义为
$$k\equiv \frac{\sqrt{ 2mE }}{\hbar}\tag{6}$$
我们需要决定散射振幅$f(\theta,\phi)$，该项决定了在$\theta,\phi$方向散射的概率（如果是完全球对称的势场将与$\phi$无关），现在有两种方法来得到

### 经典方法
以速度$v$入射，在$dt$时间内经过散射截面$d\sigma$区域的概率为
$$dP=|\psi_{incident}|^2dV=|A|^2(vdt)d\sigma$$
这个概率应该等于由势场散射到立体角$d\Omega$部分的概率：
$$dP=|\psi_{scattered}|^2dV=\frac{|A|^2|f|^2}{r^2}(vdt)r^2d\Omega$$
两者相等可以得到$d\sigma=|f|^2d\Omega$，所以
$$\boxed{D(\theta)=\frac{d\sigma}{d\Omega}=|f(\theta)|^2}\tag{7}$$

### 量子力学方法
更加准确的描述应该引入概率流密度表达式：[[概率的连续性方程]]
$$\vec{J}=-\frac{i\hbar}{2m}(\psi^*\nabla \psi-\psi \nabla \psi^*)\tag{8}$$
可以类比于连续性方程，概率流密度描述了波函数的概率分布变化趋势（是一个FLux）。现在分别计算入射通量和散射通量：
$$J_{incident}=-\frac{i\hbar}{2m}(ik-(-ik))=\frac{\hbar k}{2m}A^*A\hat{e_{z}}$$
接下来计算散射概率流密度，先将$\nabla$在球坐标下进行表示
$$\nabla=\hat{e_{r}} \frac{\partial}{\partial r}+\hat{e_{\theta}} \frac{1}{r} \frac{\partial}{\partial\theta}+\hat{e_{\phi}} \frac{1}{r\sin\theta} \frac{\partial}{\partial \phi}$$
$$\nabla \psi_{sc}=A\cdot \nabla\left( \frac{e^{ikr}}{r}f(\theta,\phi) \right)$$
所以
$$J_{scattered }=\hat{e_{r}}\left( -\frac{i\hbar}{2m} \right)(ik-(-ik))A^*\cdot A \frac{|f|^2}{r^2}=\frac{\hbar k}{m}|A|^2 \frac{|f|^2}{r^2}$$
由于
$$J_{incident} d\sigma=J_{sc}\cdot (r^2d\Omega)\Rightarrow \frac{d\sigma}{d\Omega}=|f(\theta,\phi)|^2$$
得到了与（7）相同的表达式。
接下来的工作就是确定散射振幅，我们主要有分波法（partial wave analysis）和波恩近似（Born approximation）两种方法。


## 分波法
对于球对称的势场$V(r)$我们可以将波函数写作如下形式
$$\psi(r,\theta,\phi)=R(r)Y_{l}^m(\theta,\phi)\tag{8}$$
其中$Y_{l}^m$为球谐函数，$u(r)=rR(r)$满足径向方程：
$$-\frac{\hbar^2}{2m} \frac{du^2}{dr^2}+\left[ V(r)+\frac{\hbar^2}{2m} \frac{l(l+1)}{r^2} \right]u=Eu\tag{9}$$
对于$r$很大时势能趋近于0，且离心项可以忽略，此时有
$$\frac{d^2u}{dr^2}\approx-k^2u$$
通解形式写作
$$u(r)=Ce^{ikr}+De^{-ikr}$$
第一项表示向外的球面波，第二项表示向内的球面波，显然对于散射情形第二项为0（D=0），所以对于较大的$r$：
$$R(r)\sim \frac{e^{ikr}}{r},$$
上述表达式仅对于$kr\gg 1$条件下成立，我们一般称该区域为*radiation zone*。我们合理假设势能是“localized”，即超出scattering zone的部分没有势能，仅存在离心项影响，我们称该区域为*intermediate zone*，
![[Scatter.png|400]]
此时径向方程写作：
$$\frac{d^2u}{dr^2}-\frac{l(l+1)}{r^2}u=-k^2u,\tag{10}$$
通解写作贝塞尔函数的线性组合
$$u(r)=Arj_{l}(kr)+Brn_{l}(kr)\tag{11}$$
由于$j_{l},n_{l}$都不代表向内或者向外的球面波，我们需要将其转化为类似于$e^{ikr},r^{-ikr}$的线性组合的形式，也就是*sherical Hankel functions*：
$$h_{l}^{(1)}(x)\equiv j_{l}(x)+in_{l}(x);\quad h_{l}^{(2)}(x)\equiv j_{l}(x)-in_{l}(x)\tag{12}$$
低阶Hankel functions表达式如下。
![[Hankel.png|400]]
对于较大的$r$，$h_{l}^{(1)}(kr)$趋近于$\frac{e^{ikr}}{r}$，而$h_{l}^{(2)}(kr)$趋近于$\frac{e^{-ikr}}{r}$，所以我们只需要第一类Hankel functions。
对于$V(r)=0$的exterior region，具体的波函数写作
$$\psi(r,\theta,\phi)=A\left\{ e^{ikz}+\sum_{l,m}C_{l,m}h_{l}^{(1)}(kr)Y_{l}^m(\theta,\phi) \right\}\tag{13}$$
RHS第一项为入射平面波，第二项求和项为散射球面波。对于球对称的势场，散射波应与$\phi$无关，所以只有$m=0$的项被保留：
$$Y_{l}^0(\theta,\phi)=\sqrt{ \frac{2l+1}{4\pi} }P_{l}(\cos\theta)\tag{14}$$
并将系数$C_{l,{0}}$重定义$C_{l,0}\equiv i^{l+1}k\sqrt{ 4\pi(2l+1) }a_{l}$可得
$$\boxed{\psi(r,\theta)=A\left\{ e^{ikz}+k\sum_{l=0}^\infty i^{l+1}(2l+1)a_{l} h_{l}^{(1)}(kr)P_{l}(\cos\theta) \right\}}\tag{15}$$
这里$a_{l}$被称作*partial wave amplitude*。
对于非常大的$r$，Hankel function趋近于$(-i)^{l+1}e^{ikr}/kr$，所以
$$\psi(r,\theta)\approx A\left\{ e^{ikz}+f(\theta) \frac{e^{ikr}}{r} \right\}\tag{16}$$
其中$$f(\theta)=\sum_{l=0}^\infty (2l+1)a_{l}P_{l}(\cos\theta)\tag{17}$$
现在我们可以通过分波振幅来计算$f(\theta)$，微分散射截面写作
$$D(\theta)=|f(\theta)|^2=\sum_{l}\sum_{l'}(2l+1)(2l'+1)a_{l}^*a_{l'}P_{l}(\cos\theta)P_{l'}(\cos\theta),\tag{18}$$
总散射截面为
$$\sigma=4\pi \sum_{l=0}^\infty (2l+1)|a_{l}|^2\tag{19}$$