---
title: 性質
nav_order: 4
parent: エクスパンダーグラフ
---

# 性質
エクスパンダーグラフは固有値によって定義されるが, 様々な興味深い性質を持つことが知られている. ここではグラフ理論的な性質と擬似ランダム性について紹介する.

## 擬似ランダム性
この節は高次元エクスパンダーの本筋から少し外れるが, エクスパンダーグラフの重要であることの理由の一つとしてその擬似ランダム性について概説する.

加法的組合せ論や計算量理論では**擬似ランダム性 (pseudorandomness)**と呼ばれる概念が非常に重要な役割を果たしている.

{: .definition-title }
> **定義2.4.1 (分布の擬似ランダム性)**
>
> 有限集合 $\Omega$ 上のある分布 $\mu$ と関数族 $\mathcal{F} \subseteq \{f\colon \Omega \to \binset\}$ を考える. 分布 $\mu$ は, 任意の $f\in \mathcal{F}$ に対して
>
> $$
> \abs{\E_{x\sim \mu} [f(x)] - \E_{y\sim U_{\Omega}}[f(y)]} \le \varepsilon
> $$
>
> を満たすとき, **$\mathcal{F}$に対して$\varepsilon$-擬似ランダムである**という (ここで, $y\sim U_\Omega$ とは $\Omega$ 上一様ランダムに $y$ が選ばれたことを意味する).

直感的には, 分布が擬似ランダムであるとは, その分布が任意の $f\in \mathcal{F}$ を使っても一様分布と**識別できない (indistinguishable)** ことを意味する. 例えば全変動距離に関する [命題1.2.2]({{site.baseurl}}/docs/chap1/mixing#prop:dtv) では, $\mathcal{F}$ を $V$ 上の二値関数全体 (すなわち任意の $V$ の部分集合) の族としたときの識別不可能性のパラメータ $\varepsilon$ が全変動距離で与えられることを意味する. すなわち $\mu$ は常に $\dtv(\mu,U_{\Omega})$-擬似ランダムである. 関数クラス $\mathcal{F}$ をより制限したときにパラメータ $\varepsilon$ がどこまで小さくなるかに興味がある.

組合せ論では $\mathcal{F}$ としてある特殊な関数クラスを仮定することによって**組合せ論的擬似ランダム性**を定義する. 例えばグラフ理論や加法的組合せ論のコーナーストーンの一つと呼ばれる Szemerédi の正則化補題と呼ばれる結果は, 非常に大雑把に言えば任意の密なグラフが定数個の擬似ランダムな二部グラフと疎な部分に分解できることを主張する定理である. 組合せ論的擬似ランダムネスの概念は特に加法的組合せ論において非常な協力な道具となっており, Green--Tao の定理の証明においても重要な役割を果たしている (驚くべきことに, 識別不可能性の枠組みで Green--Tao の定理の証明を理解してそれを学習理論におけるブースティングの証明に応用するという研究もなされている).

計算量理論では $\mathcal{F}$ を「効率的なアルゴリズムの全体」や「素子数の少ない論理回路の全体」とすることで**計算量的擬似ランダム性**を定義できる. 任意の効率的なアルゴリズムに対して一様ランダムな文字列と識別できないということは, その分布に従って生成されたメッセージを盗み見てもそこから得られる情報が何もない (ランダムな文字列を見てるのと同じ) であることから, 計算量的擬似ランダム性は暗号の計算量的安全性の定義の根幹をなすことがわかる.

エクスパンダーグラフの組合せ論的擬似ランダム性を説明する. 正則 $\lambda$-エクスパンダー $G=(V,E)$ を考える. 集合 $\Omega=V\times V$ 上の分布 $\mu = \mu_G$ として一様ランダムな辺 $\{u,v\}\in E$ を選び, $(u,v)$ もしくは $(v,u)$ どちらかを等確率で選んだ時の頂点対の分布とする. すなわち,

$$
\Pr_{(u,v)\sim \mu}\qty[ (u,v) = (s,t) ] = \frac{\indicator{\{s,t\}\in E}}{2\abs{E}} = \frac{\indicator{\{s,t\}\in E}}{nd} \tag{2} \label{eq:expander mu}
$$

とする. 関数族 $\mathcal{F}$ を

$$
\mathcal{F} = \set{ f_{S,T} \colon (s,t) \mapsto \indicator{s\in S,t\in T} \colon S,T\subseteq V} \tag{3} \label{eq:expander F}
$$

で定める.

以下の結果はAlonとChungによるものである[^AC88].

[^AC88]: N. Alon and F. R. K. Chung. “Explicit construction of linear sized tolerant networks”. In: Discrete Math. 72.1 (1988), pp. 15–19

<div id="lem:expander_mixing_lemma" markdown="1">
{: .lemma-title }
> **補題2.4.2 (エクスパンダー混交補題)**
>
> 任意の頂点部分集合$S,T\subseteq V$に対して,
> $e(S,T) = \sum_{s\in S,t\in T} \indicator{\{s,t\} \in E}$を$S,T$間の辺の本数($S\cap T$内の辺は2回数える)とすると,
> 
> $$
> \abs{e(S,T) - \frac{d}{n}|S||T|} \le d\lambda\sqrt{|S||T|\qty(1-\frac{|S|}{n})\qty(1-\frac{|T|}{n})}.
> $$
> 
> 同様に, $G$が片側$\lambda$-エクスパンダーならば,
> 
> $$
> e(S,T) - \frac{d}{n}|S||T| \le d\lambda\sqrt{|S||T|\qty(1-\frac{\abs{S}}{n})\qty(1-\frac{\abs{T}}{n})}.
> $$
</div>
<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
    
グラフ$G$上の単純ランダムウォーク$P$を考える. 部分集合$S,T\subseteq V$に対し関数$f=\delta_S,g=\delta_T$として
[系1.6.3]({{site.baseurl}}/docs/chap1/mixing_spectral#cor:general_expander_mixing_lemma)を適用すると
 
$$
\begin{align*}
 & \piprod{f,Pg} = \frac{e(S,T)}{nd},               \\
 & \Epi f = \frac{|S|}{n},                          \\
 & \Epi [Pg] = \Epi g = \frac{|T|}{n},              \\
 & \Varpi f = \frac{|S|}{n}\qty(1-\frac{|S|}{n}), \\
 & \Varpi g = \frac{|T|}{n}\qty(1-\frac{|T|}{n})
\end{align*}
$$
 
より整理すると主張を得る. グラフ$G$が片側エクスパンダーである場合は
代わりに
[補題1.7.2]({{site.baseurl}}/docs/chap1/other#lemma:one_side_EML)を適用すればよい.
を適用すればよい.
</details>

{: .corollary-title }
> **系2.4.3 (擬似ランダム性)**
>
> グラフ$G$が$n$頂点$d$-正則$\lambda$-エクスパンダーであるとき, (\ref{eq:expander mu})で定義された分布$\mu$は(\ref{eq:expander F})で定義された関数族$\mathcal{F}$に関して$\frac{\lambda}{4}$-擬似ランダムである.

グラフ$G$の隣接行列$A$を考えるとイメージしやすい. この行列は全部で$nd$個の$1$を持っているため, 全成分の中で$1$の密度は$\frac{d}{n}$である. ここで, 部分集合$S,T\subseteq V$に対して$A$の$S\times T$で定まる部分行列$A_{S,T}$を考える. この行列に含まれる$1$の個数($e(S,T)$に等しい)は, $\frac{d}{n}\cdot \abs{S}\abs{T}$に近い値となっている.

{: align="center"}
![text]({{site.baseurl}}/docs/images/EML.png)
{: width=100%}
<span style="font-size: 0.9em;">図: 正則グラフの隣接行列$A$を考える. このグラフがエクスパンダーならば, 頂点部分集合$S,T\subseteq V$で指定される長方形内に含まれる$1$の密度は行列全体の$1$の密度に近い値をとる.</span>

## エクスパンダー混交補題の応用

エクスパンダーグラフ上のランダムウォークはずっと同じ頂点部分集合にとどまらないことを示せる.

<div id="prop:expander_walk_hitting" markdown="1">
{: .proposition-title }
> **命題2.4.4(エクスパンダーグラフ上のランダムウォーク)**
>
> グラフ $G=(V,E)$ を $n$ 頂点 $d$-正則片側 $\lambda$-エクスパンダーとし, $(X_t)_{t\ge 0}$ を $G$ 上の単純ランダムウォークで初期頂点 $X_0$ が $V$ 上一様ランダムに選ばれたものとする. 任意の $\ell\in\Nat$ と頂点部分集合 $B\subseteq V$ に対し, $\mu = \frac{\abs{B}}{n}$ とすると, 以下が成り立つ:
>
> $$
> \Pr\qty[\text{全ての $t=0,\dots,\ell$ に対し } X_t \in B] \le \qty( \mu + \lambda(1-\mu))^\ell.
> $$
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

$\ell\ge 0$ に対し $\mathcal{E}_\ell$ を「全ての $t=0,\dots,\ell$ に対し $X_t\in B」 という事象とする. 初期頂点 $X_0$ が定常分布（＝一様分布）に従って選ばれているため, 各 $t$ に対し $X_t$ の周辺分布もまた一様分布である. 特に, 補題[2.4.2](#lem:expander_mixing_lemma)より, 任意の $t\ge 0$ に対し

$$
\Pr\qty[ X_{t+1} \in B \text{ かつ }X_t \in B] = \frac{e(B,B)}{nd} \le \mu^2 + \lambda\mu(1-\mu)
$$

を得る. 従って

$$
\begin{align*}
    \Pr\qty[\mathcal{E}_\ell] &= \Pr\qty[ X_\ell \in B \condition \mathcal{E}_{\ell-1} ]\cdot \Pr\qty[\mathcal{E}_{\ell-1}] \\
    &= \Pr\qty[X_\ell \in B \condition X_{\ell-1} \in B]\cdot \Pr\qty[\mathcal{E}_{\ell-1}] \\
    &= \frac{\Pr\qty[ X_{t+1} \in B \text{ かつ }X_t \in B]}{\mu} \cdot \Pr\qty[\mathcal{E}_{\ell-1}] \\
    &\le \qty(\mu + \lambda(1-\mu))\cdot \Pr\qty[\mathcal{E}_{\ell-1}] \\
    &\dots \\
    &\le \qty(\mu + \lambda(1-\mu))^\ell\cdot \Pr[\mathcal{E}_0] \\
    &\le \qty(\mu + \lambda(1-\mu))^\ell
\end{align*}
$$

より主張を得る.

</details>

## グラフ理論的な性質
本講義とは直接の関係はないが, エクスパンダーグラフはグラフ理論的に非常に興味深い多くの性質を有するため, いくつかを簡単に紹介する. 本節では主に正則グラフに対する組合せ論的な性質について述べる.

{: .proposition-title }
> **命題2.4.5 (低直径性)**
>
> $n$頂点$(1-\gamma)$-エクスパンダーの直径は高々$\ceil{\frac{12\log n}{\gamma}}$.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
二頂点$u,v$を任意に固定し, $u$を始点とした単純ランダムウォーク$(X_t)_{t\ge 0}$を考える. 定常分布$\pi$は$\pimin \ge \frac{1}{2|E|} \ge n^{-2}$を満たす. 従って[補題1.6.4]({{site.baseurl}}/docs/chap1/mixing_spectral#lemma:mixing_time_and_spectral_gap)を$\varepsilon=n^{-2}/2$に対して適用すると,

$$
\tmix(n^{-10}) \le \frac{4\log n}{\gamma}.
$$

$\ell=\ceil{\frac{4\log n}{\gamma}}$とする. 混交時間の定義より$\dtv(X_{\ell}, \pi) \le n^{-2}/2$であり, 任意の頂点$v\in V$に対し$\pi(v) \ge n^{-2}$なので,

$$
\Pr[X_\ell = v] \ge \pi(v) - \dtv(X_\ell,\pi) >0
$$

すなわち, 正の確率で$X_\ell = v$となるので, 特に$\dist(u,v) \le \ell$を得る. これが任意の$u,v$に対して成り立つので主張を得る.
</details>

グラフ$G = (V,E)$の頂点部分集合$S\subseteq V$は, $e(S,S)=0$, すなわち$S$内に辺が存在しないとき**独立点集合 (independent set)**いう. 独立点集合のうち最大要素数を$\alpha(G)$と表す.

{: .proposition-title }
> **命題2.4.6**
>
> 任意の$n$頂点正則$\lambda$-エクスパンダー$G$は, $\alpha(G) \le \frac{\lambda}{1+\lambda}n$を満たす.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
独立点集合$S\subseteq V$をとり, $|S|= \alpha n$とする. [補題2.4.2](#lem:expander_mixing_lemma)より,

$$
0 = e(S,S) \ge  d \alpha^2 n - d\lambda \alpha(1-\alpha) n = d\alpha n (\alpha - \lambda(1-\alpha)).
$$

すなわち$\alpha - \lambda(1-\alpha) \le 0$となり, これを解くと$\alpha\le \frac{\lambda}{1+\lambda}$を得る.
</details>

他の特に重要な性質として, **Cheegerの不等式**が知られている[^Che70]. ここでは証明は与えずに結果だけ述べる.

[^Che70]: J. Cheeger. “A Lower Bound for the Smallest Eigenvalue of the Laplacian”. Problems in Analysis. Princeton University Press, 1970, pp. 195–200.

{: .definition-title }
> **定義2.4.7 (辺膨張率)**
>
> $d$-正則グラフ$G=(V,E)$とその頂点部分集合$S\subseteq V$に対し, $S$の**辺膨張率 (edge expansion)** $\phi(S)$を
>
> $$
> \phi(S) = \frac{e(S,V\setminus S)}{d\abs{S}}
> $$
>
> で定める. グラフ$G$の辺膨張率 (または**Cheeger定数**) $\phi(G)$を
>
> $$
> \phi(G) = \min_{0 \le |S| \le |V|/2} \phi(S)
> $$
>
> とする.

$\phi(S)$の分母の値$d\abs{S}=\sum_{v\in S}\deg(v)$は$S$に接続している辺の総数に等しい ($S$内部をつなぐ辺は2回カウントされている). 分子の$e(S,V\setminus S)$はこれらのうち, $S$の外側($V\setminus S$)に接続している辺を数えている. 従って, $\phi(S)$が大きいということは, 多くの割合の辺が$S$の外側に接続していることを意味する.

{: .theorem-title }
> **定理2.4.8 (Cheegerの不等式)**
>
> 任意の正則片側$\lambda$-エクスパンダーグラフは
>
> $$
> \frac{1-\lambda}{2} \le \phi(G) \le \sqrt{2(1-\lambda)}
> $$
>
> を満たす.