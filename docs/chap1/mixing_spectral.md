---
title: ランダムウォークのスペクトルと混交時間
nav_order: 6
parent: ランダムウォーク概論
---
# ランダムウォークのスペクトルと混交時間

非自明な固有値が絶対値の意味で小さいときに混交時間が上から抑えられることを示す. 

<div id="def:second eigenvalue" markdown="1">
{: .definition-title }
> **定義1.6.1**
>
> サイズ$n$の集合$V$上の可逆なランダムウォークを考え, 
> その遷移確率行列$P$の固有値を$1=\lambda_1 \ge \dots \ge \lambda_n\ge -1$に対し, 
> $\lambda_i(P)=\lambda_i$とし, 
> $\lambda(P) \defeq \max\qty{\abs{\lambda_2},\abs{\lambda_n}}$を**非自明な第二固有値**と呼ぶ. 
> また, $\gamma\defeq 1-\lambda(P)$を**スペクトルギャップ (spectral gap)**と呼ぶ. 
</div>

遷移確率行列$P$を作用させると分散が減少する. 

<div id="lemma:variance" markdown="1">
{: .lemma-title }
> **補題1.6.2**
>
> 既約的かつ可逆なランダムウォークの
> 遷移確率行列$P$と関数$f \in \pispace$に対し
>
> $$
> (Pf)(u) \defeq \sum_{v\in V} P(u,v)f(v)
> $$
>
> とする. このとき, 
>
> $$
> \begin{align*}
>  & \Epi[Pf] = \Epi f,                            
>  & \Varpi[Pf] \le \lambda(P)^2 \cdot \Varpi [f]. 
> \end{align*}
> $$
</div>

証明は演習問題とする. 
この補題の重要な系としてエクスパンダー混交補題と呼ばれる重要な結果を得る. 

<div id="cor:general expander mixing lemma" markdown="1">
{: .corollary-title }
> **系1.6.3**
>
> 可逆なランダムウォークの遷移確率行列$P$を考える. 
> 任意の関数$f,g\in\pispace$に対し, 
>
> $$
> \abs{\piprod{f,Pg} - \Epi f \cdot \Epi g} \le \lambda(P)\cdot \sqrt{\Varpi f \cdot \Varpi g}. 
> $$
</div>

<div id="lemma:mixing time and spectral gap" markdown="1">
{: .lemma-title }
> **補題1.6.4**
>
> 集合$V$上の既約, 非周期的, 可逆なランダムウォークを考え, 
> そのスペクトルギャップを$\gamma$とする. 
> 定常分布$\pi$に対し$\pimin = \min_{u\in V} \pi(u)$とすると, 
> 任意の初期分布に対して
>
> $$
 \tmix(\varepsilon) \le \frac{\log\qty(\frac{1}{2\pimin\varepsilon})}{\log(1/\lambda(P))}. 
> $$
>
> 特に, スペクトルギャップ$\gamma>0$に対し
>
> $$
> \tmix(\varepsilon) \le \frac{1}{\gamma}\log\qty(\frac{1}{2\pimin\varepsilon}). 
> $$
>
> なお、$\log$は自然対数である. 
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

[定理1.5.4]({{site.baseurl}}/docs/chap1/pi_innerprod#thm:eigendecomposition)の正規直交基底を$x_1,\dots,x_n$とする. 
ピタゴラスの定理より任意のベクトル$f \in \Real^V$は

$$
\pinorm{f}^2 = \sum_{i=1}^n \piprod{f,x_i}^2
$$

を満たす. 
特に, 頂点$u$を固定し$f$としてディラック測度$f=\delta_u$とすると

$$
\begin{align*}
  \pi(u) & = \pinorm{\delta_u}^2                                                    \\
       & = \sum_{i=1}^n \piprod{\delta_u,x_i}^2                                       \\   
       & = \sum_{i=1}^n \pi(u)^2x_i(u)^2                                                \\ 
       & = \pi(u)^2 + \pi(u)^2\sum_{i=2}^n x_i(u)^2 &  & \text{($\because x_1=\allone$)}
\end{align*}
$$

を得る. 
特に, $\sum_{i=2}^n x_i(u)^2 = \frac{1}{\pi(u)} - 1 \le \frac{1}{\pi(u)}$である. 

ここで, [定理1.5.4]({{site.baseurl}}/docs/chap1/pi_innerprod#thm:eigendecomposition)より, $P^t\Pi^{-1} - J$の第$(u,v)$成分に着目すると

$$
\begin{align*}
  \abs{\frac{P^t(u,v)}{\pi(v)} - 1} & \le \sum_{i=2}^n \abs{\lambda_i}^t \abs{x_i(u)x_i(v)}\\
                     & \le \lambda^t  \sqrt{\sum_{i=2}^n x_i(u)^2} \sqrt{\sum_{i=2}^n x_i(v)^2} &  & \text{$\because$Cauchy-Schwarzの不等式} \\
                     & \le \frac{\lambda^t}{\sqrt{\pi(u)\pi(v)}}        \\                                                      
                     & \le \frac{\lambda^t}{\pimin}
\end{align*}
$$

を得る. 
特に, 任意の頂点$u\in V$に対して

$$
\dtv\qty(P^t(u,\cdot),\pi) = \frac{1}{2}\sum_{v\in V} \abs{P^t(u,v) - \pi(v)} \le \frac{\lambda^t}{2\pimin}
$$

なので, 任意の初期分布に対して混交時間は

$$
\tmix(\varepsilon) \le \inf\qty{t\ge 0\colon \frac{\lambda^t}{2\pimin} \le \varepsilon} \le \frac{\log\qty(\frac{1}{2\pimin\varepsilon})}{\log(1/\lambda(P))} \le \frac{1}{\gamma}\log\qty(\frac{1}{2\pimin\varepsilon}). 
$$

最後の不等式では${}^\forall x\in \Real,x\le \mathrm{e}^{x-1}$を用いた. 

</details>
