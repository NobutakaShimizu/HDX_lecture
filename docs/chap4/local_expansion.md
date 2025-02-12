---
title: 局所エクスパンダー性
nav_order: 3
parent: マトロイド
---

# マトロイドの局所エクスパンダー性

本節では以下の定理を証明します.

<div id="lem:local_expander_matroid" markdown="1">
{: .lemma-title }
> **補題4.3.1**
> 
> 任意のマトロイド$(V,\F)$は局所$0$-エクスパンダーである.
</div>

## Oppenheimのトリクルダウン定理

ある単体複体$X$に対して局所エクスパンダー性を示すには全ての面に対して$\lambda_2(P_\sigma)$を上から抑える必要があります.
一般にそもそも辺重み$w_\sigma$を求めることすら非自明であり, ましてや固有値を抑えるなど非常に大変な作業となります.
Oppenheimのトリクルダウン定理は局所エクスパンダー性を確認するのに非常に有用な定理です.

<div id="thm:Oppenheim_trickle-down_theorem" markdown="1">
{: .theorem-title }
> **定理4.3.2 (Oppenheimのトリクルダウン定理)**
>
> 純粋な重み付き$d$-次元単体複体$X = (V,\F)$が以下の二つを満たすとします:
> - 全ての$i\le d-2$と全ての$\sigma\in X(i)$に対してグラフ$G_\sigma$は連結。
> - 全ての$(d-2)$-次元の面$\tau \in X(d-2)$に対して$\lambda_2(P_\tau) \le \gamma$。
>
> このとき、$\gamma_i \defeq \frac{\gamma}{1-(d-2-i)\gamma}$ ($i=-1,\dots,d-2$)に対して$X$は局所$(\gamma_{-1},\dots,\gamma_{d-2})$-エクスパンダーである。
</div>

端的に言えば、次数$d-2$の面$\sigma \in X(d-2)$に対して$\lambda(P_\sigma)$を抑えれば全ての次元の面に対しても第二固有値が上から抑えられるという結果です。
最上次元の面のエクスパンダー性が下次元の面に波及していくという意味ではまさに「トリクルダウン(浸透)」と言えます。

一つ目のグラフ$G_\sigma$の連結性の条件は不可欠です。
例えば二つの完全グラフからなる非連結グラフ上の三角形複体を考えると、
空集合以外の全てのリンクは完全グラフ上のランダムウォークとなるため$\gamma=0$に対して二つ目の条件を満たしますが、$\sigma=\emptyset$に対して$G_\sigma$は非連結であるため$\gamma_{-1}=0$にはなりません。

## トリクルダウン定理の証明 ($d=2$)

まず$d=2$の特殊ケースで[トリクルダウン定理](#thm:Oppenheim_trickle-down_theorem)を証明します。

<div id="lem:trickle_down_2dim" markdown="1">
{: .lemma-title }
> **補題4.3.3 ($d=2$におけるトリクルダウン定理)**
>
> 純粋な重み付き$2$次元単体複体$X=(V,\F)$の各頂点$v\in X(0)$における局所ランダムウォーク$P_v$が$\lambda_2(P_v) \le \gamma$を満たし、かつその$1$-スケルトン$G_vが連結ならば、面$\emptyset$における局所ランダムウォーク$P_\emptyset$は
>
> $$
\lambda_2(P_\emptyset) \le \frac{\gamma}{1-\gamma}
> $$
>
> を満たします。
</div>

この補題は本質的に$\gamma<1/2$のときに意味をなします。

[補題4.3.3](#lem:trickle_down_2dim)の証明はランダムウォークを分解することから始まります。
記法の簡単のため、頂点$u$のリンクを$X_{\{u\}}$の代わりに$X_u$、遷移確率行列を$P_{\{u\}}$の代わりに$P_u$と表します。

<div id="def:localize" markdown="1">
{: .definition-title }
> **定義4.3.4**
>
> 重み付き単体複体$(V,\F)$、頂点$u\in V$、関数$f \in \ispace{X(0)}$に対し、関数$f^u \in \ispace{X_u(0)}$を$f$の$X_u(0)$への制限、すなわち
>
>$$
f^u (v) = f(v)
>$$
>
>とします。
</div>

簡単な計算から以下の二次形式の分解補題が成り立つことがわかります。

<div id="lem:decomposition" markdown="1">
{: .lemma-title }
> **補題4.3.5**
>
> 任意の$f,g\in \ispace{X(0)}$に対して
>
> $$
\iprod{X(0)}{f,g} = \E_{u\sim X(0)}\qty[ \iprod{X_u(0)}{f^u,g^u} ]。
> $$
>
> また、面$\emptyset$上の局所ランダムウォークの遷移確率行列を$P_\emptyset \in [0,1]^{X(0)\times X(0)}$とすると、
>
> $$
\iprod{X(0)}{P_\emptyset f,g} = \E_{w\sim X(0)}\qty[ \iprod{X_u(0)}{P_uf^u,g^u} ]。
> $$
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
    
最初の等式を示します:

$$
\begin{align*}
(\textの左辺) &= \E_{u\sim X(0)} \qty[ f(u) g(u) ] \\
&= \E_{e \sim X(1)}\qty[ \E_{v \sim e} \qty[f(v)g(v)]] & & \text{$v\sim e$の周辺分布は$\pi_0$}\\
&= \E_{u\sim X(0)} \qty[ \E_{\substack{e=\{u,v\} \sim X(1) \\ \text{conditioned on }e\ni u}} \qty[ f(v)g(v) ]] & & \text{$e\sim X(1)$の$v$でない方の端点$u$を先に選ぶ}\\
&= \E_{u\sim X(0)}\qty[ \E_{v \sim X_u(0)} \qty[f^u(v) g^u(v)] ] & & \text{$\because$\cref{rem:link of u}}\\
&= (\textの右辺)。
\end{align*}
$$

二つ目の等式を示します。

$$
\begin{align*}
(\textの左辺) &= 
\E_{\substack{u\sim X(0)\\ v\sim P_\emptyset(u,\cdot)}} \qty[ f(u)g(v)]\\
&= \E_{t \sim X(2)}\qty[ \E_{\substack{w \sim t \\ u \sim t\setminus \{w\}, \\ \{v\}=t\setminus\{u,w\}}} \qty[f(u)g(v)] ] \\
&= \E_{w\sim X(0)}\qty[ \E_{\substack{t \sim X(2) \\ \text{conditioned on }t \ni w \\ u \sim t\setminus w \\ \{v\}=t\setminus\{u,w\}}} \qty[f(u)g(v)] ] & & \textの前式の$w$の周辺分布は$X(0)$\\
&= \E_{w\sim X(0)}\qty[ \E_{\substack{u\sim X_w(0) \\ v\sim P_w(u,\cdot)}}\qty[f(u)g(v)] ] \\
&= (\textの右辺)。
\end{align*}
$$

</details>

これを使って[補題4.3.3](#lem:trickle_down_2dim)を証明します。

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">補題4.3.3の証明</summary>
    
記号の簡単のため$P=P_\emptyset$とします。
局所ランダムウォーク$P$の第二固有値に対応する固有ベクトルを$f$とします。
正規化して$\inorm{X(0)}{f}=1$とします。
$P_\emptyset$の可逆性および[レイリー商の補題]({{site.baseurl}}/docs/chap1/other#lemma:Rayleigh_quotient)から、$\iprod{X(0)}{f,\allone}=0$である。
補題を証明するには、$ \lambda_2(P)=\iprod{X(0)}{P f,f}$を上から抑えればよいです。
各頂点$u \in X(0)$に対し[定義4.3.4](#def:localize)で定義された$f^u \in \ispace{X_u(0)}$を考えます。
このベクトルを直交分解し、

$$
\begin{align}
f^u = \alpha_u \allone^u + \overline{f^u} \tag{1} \label{eq:eigen_decomposition_fu}
\end{align}
$$

と表します。
ここで、$\allone^u \in \ispace{X_u(0)}$は全成分が$1$のベクトルで、$\alpha_u=\iprod{X_u(0)}{f,\allone^u}$であり、$\overline{f^u}$は$\allone^uに直交するベクトルである。

直交分解(\ref{eq:eigen_decomposition_fu})を用いて二次形式を計算すると

$$
\begin{align*}
\iprod{X_u(0)}{P_u f^u,f^u} &= \iprod{X_u(0)}{P_u\qty(\alpha_u\allone^u + \overline{f^u}), \alpha_u\allone^u+\overline{f^u}} \\
&= \alpha_u^2 + \iprod{X_u(0)}{P_u\overline{f^u},\overline{f^u}} \\
&\le \alpha_u^2 + \gamma\inorm{X_u(0)}{\overline{f^u}}^2 & & \because \lambda_2(P_u)\le\gamma
\end{align*}
$$

を得ます。　[補題4.3.5](#lem:decomposition)より

$$
\begin{align*}
\lambda_2(P) &= \iprod{X(0)}{Pf,f} \\
&= \E_{u\sim X(0)}[ \iprod{X_u(0)}{P_u f^u,f^u} ] & & \textの補題4.3.5の二つ目の等式\\
&\le \E_{u\sim X(0)}[\alpha_u^2] + \gamma\cdot \E_{u\sim X(0)}[\inorm{X_u(0)}{\overline{f^u}}^2] & & 直前の不等式を代入\\
&= \gamma\cdot \E_{u\sim X(0)}[\alpha_u^2 + \inorm{X_u(0)}{\overline{f^u}}^2] + (1-\gamma)\cdot \E_{u\sim X(0)}[\alpha_u^2] \\
&= \gamma\cdot \E_{u\sim X(0)}[\inorm{X_u(0)}{f^u}^2] + (1-\gamma)\cdot \E_{u\sim X(0)}[\alpha_u^2] & & $f^u$に対する三平方の定理\\
&= \gamma \cdot \inorm{X(0)}{f}^2 + (1-\gamma)\cdot \E_{u\sim X(0)}[\alpha_u^2] & & 補題4.3.5\\
&= \gamma + (1-\gamma)\cdot \E_{u\sim X(0)}[\alpha_u^2] & & $f$のノルムは$1$
\end{align*}
$$

を得ます。従って、$\E_{u\sim X(0)}[\alpha_u^2]$を上から抑えたいです。

内積$\iprod{X_u(0)}{\cdot,\cdot}$ の定義から

$$
    \begin{align*}
        \alpha_u &= \iprod{X_u(0)}{f^u,\allone^u} \\
        &= \E_{v\sim X_u(0)}[f^u(v)] \\
        &= \E_{v\sim X_u(0)}[f(v)] \\
        &= (Pf)(u) & & $P=P_\emptyset$は$1$-スケルトン上のランダムウォーク
    \end{align*}
$$

であり、$f$は$P$の固有ベクトルなので

$$
    \begin{align*}
        \E_{u\sim X(0)}[\alpha_u^2] = \inorm{X(0)}{Pf}^2 = \lambda_2(P)^2。
    \end{align*}
$$

これを代入すると、二次不等式

$$
    \begin{align*}
        \lambda_2(P) &\le \gamma + (1-\gamma)\cdot \lambda_2(P)^2
    \end{align*}
$$

を得ます。これを$\lambda_2(P)$について解くと

$$
    \begin{align*}
        \lambda_2(P)\ge 1 または \lambda_2(P) &\le \frac{\gamma}{1-\gamma}
    \end{align*}
$$

となりますが、$1$-スケルトンの連結性の仮定より$\lambda_2(P)<1$なので、$\lambda_2(P)\le\frac{\gamma}{1-\gamma}$を得ます。

</details>

## トリクルダウン定理の証明(一般の$d$)

[補題4.3.3](#lem:trickle_down_2dim)を使って一般の$d$について[定理4.3.2](#thm:Oppenheim_trickle-down_theorem)を証明します。

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">定理4.3.2の証明</summary>

$X=(V,\F)$を純粋な重み付き$d$次元単体複体とします ($d\ge 3$)。
面$\sigma\in X(d-3)$のリンク$X_\sigma$の次元は$2$であり、
$X_\sigma$の頂点$v\in X_\sigma(0)$に対して
$\sigma\cup\set{v} \in X(d-2)$
より、$X_\sigma$上の$v$における局所ランダムウォークの遷移確率行列は$P_{\sigma\cup\set{v}}$に等しく、
仮定より$\lambda_2(P_{\sigma\cup\set{v}})\le \gamma$である。
さらに、$X$の各リンクの$1$-スケルトンは連結なので、[補題4.3.3](#lem:trickle_down_2dim)より

$$
    \begin{align*}
        \lambda_2(P_\sigma) &\le \frac{\gamma}{1-\gamma}
    \end{align*}
$$

を得ます。同じ議論を、$X$をその$(d-1)$-スケルトンに置き換えて適用すると、任意の$\sigma'\in X(d-4)$に対し

$$
    \begin{align*}
        \lambda_2(P_{\sigma'}) &\le \frac{\frac{\gamma}{1-\gamma}}{1-\frac{\gamma}{1-\gamma}} \le \frac{\gamma}{1-2\gamma}
    \end{align*}
$$

を得ます。これを繰り返すと、$j$に関する帰納法により、任意の面$\rho \in X(d-2-j)$に対し

$$
    \begin:align*}
        \lambda_2(P_\rho) \le \frac{\gamma}{1-j\gamma}
    \end:align*}
$$

を得ます。

</details>
