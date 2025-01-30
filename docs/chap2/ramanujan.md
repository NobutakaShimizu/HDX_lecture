---
title: ラマヌジャングラフ
nav_order: 3
parent: エクスパンダーグラフ
---

# ラマヌジャングラフ
グラフの辺数を固定したとき, エクスパンダー性のパラメータ$\lambda$はどこまで小さくできるだろうか? ここでは厳密な証明は与えずに直感的な議論によって正則グラフに絞ってエクスパンダー性の限界を説明する。

応用上は正則なエクスパンダーグラフが重要である。正則グラフ上のランダムウォークの遷移確率行列は単に隣接行列を次数で割ったものであり定常分布も一様分布なので単に隣接行列の固有値を考えれば良いことがわかる。

固定した自然数$d\ge 3$に対して最もエクスパンダー性の強い(つまり$\lambda$が最小となる)$d$-正則グラフはどのようなグラフだろうか? 問題を言い換えればランダムウォークがより多くの頂点を訪れやすくするにはグラフをどのように構成すれば良いだろうか?

## 理想的なグラフ: $d$-正則無限木
直感的な議論だが, 短い閉路があるとそれに沿って同じ頂点を訪れてしまうので, そのような閉路はない方が良いと思われる。従ってそのグラフを虫眼鏡でズームすると局所的には木構造になっているべきであろう。そこで「理想的な」グラフとして$d$-正則で頂点数が無限の木$T$を考える。頂点集合$V$は可算無限であるため, 有限グラフに対する隣接行列や固有値の概念を無限グラフに拡張したものが必要である。集合$\ell^2(V) \subseteq \Real^V$を
$\ell^2(V) = \set{ f \colon V \to \Real\colon \sum_{u\in V}f(u)^2 < \infty }$とする。隣接作用素$A\colon \ell^2(V) \to \ell^2(V)$を

$$
  A f(u) = \sum_{v \in N_T(u)} f(v)
$$

で定める (ただし$N_T(u)$は$u$の隣接頂点の集合)。

$T$の$d$-正則性から$N_T(u)$は有限集合である.
有限グラフの文脈では$\allone$が第一ベクトルとなっていたが, 無限グラフの文脈では$\allone$は$\ell^2(V)$に属さないため,
自明な固有値を自然に除外して議論できるのである!
作用素$A$のスペクトルを

$$
  \mathrm{spec}(A) = \set{ \lambda \in \Real \colon A - \lambda I\text{ は退化}}
$$

とする。

{: .theorem-title }
> **定理2.3.1 (無限$d$-正則木のスペクトル)**
>
> $d$-正則無限木$T$の隣接作用素$A$のスペクトルは以下を満たす:
>
> $$ \mathrm{spec}(A) \subseteq [-2\sqrt{d-1}, 2\sqrt{d-1}]. $$


従って, 理想的なグラフを考えるとその隣接行列の非自明な固有値はその絶対値が高々$2\sqrt{d-1}$である (第一固有ベクトル$\allone$に対応する関数は$\ell^2(V)$に属さない)。よって任意の$d$-正則グラフは$\lambda(P)\ge \frac{2\sqrt{d-1}}{d}$を満たすであろうことが予想される。

## Alon-Boppanaの定理

Alon-Boppanaの定理とは, 無限$d$-正則木のスペクトルが有限の$d$-正則グラフのエクスパンダー性の限界を与えることを主張する定理です.

<div id="thm:Alon Boppana" markdown="1">
{: .theorem-title }
> **定理2.3.2 (Alon--Boppanaの定理)**
>
> ある定数 $c>0$ が存在し、任意の $n$ 頂点 $d$ 正則グラフ $G$ 上の単純ランダムウォークの遷移確率行列 $P$ の第二固有値 $\lambda_2$ は
>
> $$
> \lambda_2 \ge \frac{2\sqrt{d-1}}{d}\qty( 1 - \frac{c}{\diam(G)^2})
> $$
>
> を満たす。
</div>

特に, 以下の命題により$d$が定数のとき$d$-正則グラフの直径$\diam(G)$は$\diam(G)=\Omega(\log n)$となるので,
Alon-Boppanaの定理により$\lambda_2 \ge (1-o(1))\frac{2\sqrt{d-1}}{d}$となることがわかる.

<div id="prop:regular diameter" markdown="1">
{: .proposition-title }
> **命題2.3.3**
>
> $d \ge 3$ のとき、$n$ 頂点 $d$-正則連結グラフ $G=(V,E)$ の直径は $\diam(G) \ge \log_{d-1}\frac{(d-2)(n-1)}{d}$ を満たす。
</div>
<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

  頂点 $u \in V$ を固定すると、$u$ から $\ell$ 本以下の辺を辿って辿り着ける頂点は高々


$$
    \begin{align*}
        1 + d + d(d-1) + \dots + d(d-1)^{\ell-1} &\le 1 + d(d-1)^{\ell-1}\sum_{i=0}^{\ell-1}\qty(\frac{1}{d-1})^i \\
        &\le 1+\frac{d(d-1)^\ell}{d-2}.
    \end{align*}
$$


  この最右辺が $n$ より真に小さいとき、$u$ から $\ell$ 本以下の辺を辿って辿り着けない頂点が存在する。従って、$\ell=\diam(G)$ を代入したときの最右辺は $n$ 以上でなければならないため、不等式
  
  $$
  1+\frac{d(d-1)^{\diam(G)}}{d-2}\ge n
  $$
  
  を解くと主張を得る。

</details>

[Alon-Boppanaの定理](#thm:Alon Boppana)を証明するために以下の補題を準備する.

<div id="lem:closed walk regular graph" markdown="1">
{: .lemma-title }
> **補題2.3.4 (正則グラフの閉路数の下界)**
>
> $d\ge 3$に対し, $T$を$d$-正則無限木とし, 頂点を一つ固定する.
> この頂点を含む長さ$2k$の閉路の個数を$t_{2k}$とすると
>
> $$
> t_{2k} \ge (d-1)^{k}\cdot \frac{1}{k+1}\binom{2k}{k}
> $$
>
> である.
> さらに,
> 任意の$d$-正則グラフ$G=(V,E)$の任意の頂点$u$に対し, $u$を含む長さ$2k$の閉路の個数は少なくとも$t_{2k}$である.
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
$d$-正則無限木$T$の特別な頂点$v_0$を一つ固定し、(グラフ理論においてスタンダードな)幾つかの用語を定義する。
固定した特別な頂点$v_0$を**根 (root)**と呼び、
$T$の頂点$v$に対し、$\dist(v_0,v)$を**深さ (depth)**と呼び$\mathrm{depth}(v)$で表す (特に$\mathrm{depth}(v_0)=0$である)。
頂点$v$に$T$上で隣接している$d$個の頂点からなる集合を$N_T(v)$と表す ($N_T(v)$に$v$は含めない)。
これらの隣接頂点のうち、深さが$\mathrm{depth}(v)-1$となるただ一つの頂点を$v$の**親 (parent)**と呼び、
残りの深さ$\mathrm{depth}(v)+1$の頂点を$v$の**子 (child)**と呼ぶ。

![3正則木]({{site.baseurl}}/docs/images/tree.png)
<span style="font-size: 0.9em;">図: $3$正則木$T$上の長さ$10$の閉路。親から子への遷移と子から親への遷移を$5$回ずつ行う。右図は深さ$d_i$の遷移を表す。</span>

木$T$において根を始点とする長さ$2k$の閉路$(v_0,\dots,v_{2k})$を考える (ここで$v_0=v_{2k}$)。
各$i$に対して$d_i = \mathrm{depth}(v_i)$とし、列$(d_0,\dots,d_{2k})$を考える。
まず$d_0=0$であり、その後は$d_{i+1} \in \set{d_i \pm 1}$であり、常に非負を保ちながら最後に$d_{2k}=0$となる。
このような列$(d_0,\dots,d_{2k})$の総数はカタラン数と等しく、$\frac{1}{k+1}\binom{2k}{k}$に等しい。
特に、各$d_i - d_{i-1}$の符号を見ると$d_0 = d_{2k} = 0$より正と負がそれぞれ$k$個ずつ含まれている。

次に、各$(d_1,\dots,d_{2k})$に対して深さの履歴がこれと等しくなるような閉路の個数を考える。
各$i\ge 2$において、$d_i=d_{i-1}+1$ (すなわち$v_i$が$v_{i-1}$の子である)とき、$v_i$の選び方は少なくとも$d-1$通りある ($v_i$が根であるときは$d$通りあるがこれも下から$d-1$で抑える)。
一方で親に遷移する場合はその遷移先は一意である。
子への遷移はちょうど$k$回発生するため、深さの履歴が与えられた$(d_1,\dots,d_{2k})$に等しくなるような閉路の個数は少なくとも$(d-1)^{k}$個存在する。
従って$t_{2k} = \frac{1}{k+1}\binom{2k}{k} \cdot (d-1)^{k}$を得る。

後半の主張を証明する。
$d$-正則グラフ$G$の頂点$u_0$を一つ固定する。
木$T$の頂点集合を$U$、グラフ$G$の頂点集合を$V$とし、
$N_T$の定義と同様にグラフ$G$の頂点$v \in V$に対しその$d$個の隣接頂点の集合を$N_G(v)$で表す。
$G$から$T$への準同型写像$\phi \colon U \to V$を以下のように構成する(グラフ$G=(V,E)$から$H=(W,F)$への**準同型写像 (homomorphism)**とは、写像$\phi\colon V\to W$であって$\{u,v\}\in E\Rightarrow \{\phi(u),\phi(v)\}\in F$を満たすものである。ここでは自然に無限グラフに対してこの概念を拡張している).
深さに関して帰納的に定義する:

- まず、$\phi(v_0) = u_0$とする。
    根$v_0$の子$N_T(v_0)$から$N_G(u_0)$への全単射$\phi_0$を任意に一つ選び、
    $\phi\colon N_T(v_0) \ni v' \mapsto \phi_1(v') \in N_T(u_0)$
    によって$N_T(v_0)$における$\phi$を定義する。
- $T$における深さ$\ell$以下の全ての頂点に対し$\phi(v)$が定義されているとする。深さ$\ell$の各頂点$v$に対し、その親を$p$、子を$c_1,\dots,c_{d-1}$とする。$v$とその親$p$に対しては$u\defeq \phi(v)$、$u_p\defeq \phi(p)\in U$が定義されている。このとき、全単射$\psi\colon N_T(v)\setminus \{p\} \to N_G(u)\setminus\{u_p\}$を任意に一つ固定し、各$\phi(c_j)$を$\psi(c_j)\in V$とする。

このようにして定義された写像$\phi\colon U \to V$は確かに準同型なので
$T$の閉路$(v_0,\dots,v_{2k})$に対して$(\phi(v_0),\dots,\phi(v_{2k}))$は$G$の閉路になっている。
さらに、$(\phi(v_0),\dots,\phi(v_{2k}))$の形になっている$G$の閉路が与えられたとき、$v_0$は一意に定まり、以降の$v_i$は$\phi$の帰納的な定義で用いた全単射の逆写像を用いて順番に復元することができるため、$(v_0,\dots,v_{2k}) \mapsto (\phi(v_0),\dots,\phi(v_{2k}))$は単射である。
従ってグラフ$G$に含まれるある頂点を始点とした長さ$2k$の閉路の個数は少なくとも$t_{2k}$である。
\end{proof}

</details>

本講義では, [定理2.3.2](#thm:Alon Boppana)より少し弱い下界として

$$
\begin{align}
  \lambda_2 \ge \frac{2\sqrt{d-1}}{d}\qty(1 - O\qty(\frac{\log \diam(G)}{\diam(G)})) 
    \tag{1}
  \label{eq:weak alon boppana bound}
\end{align}
$$

を証明する。この下界でも $\lambda_2 \ge \frac{2\sqrt{d-1}}{d}(1-o(1))$ を示すには十分である。

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">(\ref{eq:weak alon boppana bound})の証明</summary>

遷移確率行列を$P$とし, 隣接行列を$A$とする.
二頂点$u,v$を$uv$間の最短路が$\diam(G)$に等しくなるように固定し
関数$f \colon V \to \Real$を$f = \delta_s - \delta_t$とすると, 任意の$k\ge 1$に対して,
[補題1.6.1]({{site.baseurl}}/docs/chap1/other#lem:Rayleigh quotient)より

$$
\begin{align*}
    \lambda(P^{2k}) & = \lambda(P^k)^2                                                                                                \\
                    & \ge \frac{\piprod{f,P^{2k} f}}{\pinorm{f}^2}                  &  & \text{$\because$補題1.6.1} \\
                    & = \frac{P^{2k}(u,u) + P^{2k}(v,v) - 2P^{2k}(u,v)}{2}                                                            \\
                    & = \frac{A^{2k}(u,u) + A^{2k}(v,v) - 2A^{2k}(u,v)}{2d^{2k}}. &  & \text{$\because P=\frac{1}{d}A$}
\end{align*}
$$

[補題1.3.2]({{site.baseurl}}/docs/chap1/random_walk_on_graph#lem:adjacency walk count})より, $k=\floor{\frac{\diam(G)-1}{2}}$とすると, $u,v$の選び方より$A^{2k}(u,v)=0$である.
また, $A^{2k}(u,u)$は頂点$u$を含む長さ$2k$の閉路の個数に等しい.
さらに, この値は$d$-正則無限木$T$において固定した頂点を含む長さ$2k$の閉路の個数で下から抑えることができる.

二項係数$\binom{2k}{k}$はStirlingの近似により$\binom{2k}{k} \ge \frac{4^k}{\sqrt{\pi k}}\qty(1-\frac{1}{8k})$を満たすことが示せる.
従って, [補題2.3.4](#lem:closed walk regular graph)より,

$$
\begin{align*}
    \lambda(P)^{2k} & \ge d^{-2k} t_{2k}                                                                     \\
                    & \ge d^{-2k}\cdot (d-1)^k \cdot \frac{2^{2k}}{(k+1)\sqrt{\pi k}}\qty(1-\frac{1}{8k}).
\end{align*}
$$

特に, ある定数$c>0$が存在して

$$
\begin{align*}
    \lambda(P) & \ge \frac{2\sqrt{d-1}}{d} \cdot k^{-c/k}                            \\
                & \ge \frac{2\sqrt{d-1}}{d}\cdot \qty(1-O\qty(\frac{\log k}{k})).
\end{align*}
$$

最後の不等号は$k^{-k}=\e^{-\frac{\log k}{k}} = 1-O\qty(\frac{\log k}{k})$を用いた.
$k=\floor*{\frac{\diam(G)-1}{2}}$を代入すれば(\ref{eq:weak alon boppana bound})を得る.
</details>



## ラマヌジャングラフの定義

漸近的に[定理2.3.2](#thm:Alon Boppana)を達成するグラフを**ラマヌジャングラフ (Ramanujan graph)**という。

{: .definition-title }
> **定義2.3.5 (ラマヌジャングラフ)**
>
> $d$-正則グラフ$G=(V,E)$は、単純ランダムウォークの遷移確率行列$P$の第二固有値$\lambda_2$が$\lambda_2 \le 2\sqrt{d-1}$を満たすとき、**ラマヌジャングラフ (Ramanujan graph)**という。

[定理2.3.2](#thm:Alon Boppana)を達成するグラフ列、すなわち、次数$d$を固定したときに頂点数が増大していくグラフ列$(G_n)_{n\in\Nat}$であって各$G_n$が$d$-正則ラマヌジャングラフとなるものは存在するだろうか？この漸近的に最適な正則エクスパンダーグラフの構成は\citet{LPS88,Mar88}によって独立同時期に初めてその構成が与えられた。彼らは$d-1$が$4$で割った余りが$1$となる素数であるときに$d$-正則ラマヌジャングラフの列を構成した。なお、「ラマヌジャングラフ」という名称は\cite{LPS88}の証明がラマヌジャン予想と呼ばれる予想に依拠しているからである（「予想」と書いたが当時は既に解決している）。その後、\citet{Mor94}によって次数が素数べき$+1$の形であってもラマヌジャングラフが構成できることが示された。

{: .theorem-title }
> **定理2.3.6 (ラマヌジャングラフの陽な構成)**
>
> 任意の素数$q$と任意の$k\in\Nat$に対して、頂点数が発散するある$(q^k+1)$-正則ラマヌジャングラフの列が存在し、陽に構成できる。