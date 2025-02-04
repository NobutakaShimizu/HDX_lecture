---
title: グラフ上のランダムウォーク
nav_order: 3
parent: ランダムウォーク概論
---
# グラフ上のランダムウォーク

まずグラフ理論の基礎的な概念の定義を与える。読者は[単純ランダムウォーク](#単純ランダムウォーク)まで読み飛ばし, 必要に応じて後から定義を参照してもよい.

{: .definition-title }
> **定義1.3.1(グラフ)**
>
> 有限単純無向グラフを単に**グラフ (graph)**と呼ぶ. すなわち, グラフとは有限集合$V$とその二元部分集合$E\subseteq \binom{V}{2}$の組 $G = (V, E)$ である.$V$の元を**頂点(vertex)**, $E$の元を**辺(edge)**と呼ぶ.
>
> - 二頂点$u,v\in V$が$\{u,v\}\in E$を満たすとき, $u$は$v$に**隣接 (adjacent)**しているという ($v$もまた$u$に隣接している). 頂点$u$と辺$e\in E$が$u\in e$を満たすとき, $e$は$u$に**接続 (incident)**しているという. 頂点$u$に接続している辺の本数を$u$の**次数(degree)**といい, $\deg(u)$で表す. 全ての頂点の次数が$d$に等しいとき, $G$は**$d$-正則 ($d$-regular)**であるという.
> - 二つのグラフ$G=(V,E),H=(U,F)$に対して$U\subseteq V,F\subseteq E \cap \binom{U}{2}$を満たすとき$G$は$H$を**部分グラフ (subgraph)**として含むといい, $H\subseteq G$で表す. 特に$F=\binom{U}{2}\cap E$となる部分グラフを誘導部分グラフと呼び, $G[U]$と表す.
> - 隣接行列$A \in \Real^{V\times V}$を以下で定義する:
>
  $$
    A(u,v) = \indicator{\{u,v\}\in E} =
    \begin{cases}
      1 & \text{if }\{u,v\}\in E, \\
      0 & \text{otherwise}.
    \end{cases}
  $$
>
> - 頂点列$(v_0,\dots,v_\ell) \in V^{\ell+1}$は$\{v_0,v_1\},\dots,\{v_{\ell-1},v_\ell\}\in E$を満たすとき, $v_0$から$v_\ell$への**路 (walk)** といい, $\ell$を長さと呼ぶ. 路$(v_0,\dots,v_\ell)$に対し$v_0$と$v_\ell$をそれぞれ始点, 終点と呼ぶ. 路$(v_0,\dots,v_\ell)$が$v_0=v_\ell$であって満たすものを**閉路 (cycle)**という.
> - 二頂点$u,v \in V$に対し, $u$から$v$への路が存在しかつそのときに限り$u\sim v$とすることで頂点集合$V$上の同値関係$\sim$を定義する. このとき, 商集合$V / \sim$の各同値類を$G$の**連結成分 (connected component)**という. 商集合$V / \sim$が単一の連結成分からなるとき, $G$は**連結 (connected)**であるという.
> - 二頂点$u,v$の間の**距離 (distance)**を, $uv$間の路のうちの最小長さで定義し, $\dist(u,v)$で表す($uv$路が存在しない場合は$\dist(u,v)=\infty$とする). グラフ$G$の**直径 (diameter)**を$\diam(G)=\max_{u,v\in V}\dist(u,v)$で定める.
> - グラフ$G=(V,E)$を考える. 二頂点$u,v \in V$に対し, $u$から$v$への路が存在しかつそのときに限り$u\sim v$とすることで頂点集合$V$上の同値関係$\sim$を定義する. このとき, 商集合$V / \sim$の各同値類を$G$の**連結成分 (connected component)**という. 商集合$V / \sim$が単一の連結成分からなるとき, $G$は**連結 (connected)**であるという.
> - グラフ$G=(V,E)$を考える. ある頂点分割$V=L\sqcup R$が存在して$E\cap \binom{L}{2}=\emptyset$かつ$E\cap \binom{R}{2}=\emptyset$が成り立つとき, $G$は**二部 (bipartite)**であるといい, 頂点部分集合$L,R$を$G$の**部集合 (partite set)**と呼ぶ.

路とは辺を辿って始点から終点に至るまでの経路を表す. なお, 同じ頂点や辺を2回以上通ってもよいことに注意せよ.

直感的には, $G$が二部グラフであるというのは, ある頂点分割$V=L\sqcup R$に対して$G$の全ての辺が$L$と$R$の間を跨いでいることを意味する. なお, 部集合への分割$V = L\sqcup R$は必ずしも一意であるとは限らない. よく知られる事実として, グラフ$G$が二部グラフであることの必要十分条件は$G$の全ての閉路の長さが偶数であることである.

隣接行列$A$に対し, $A^\ell$の各成分は長さ$\ell$の路の個数に等しい.

<div id="lem:adjacency_walk_count" markdown="1">
{: .lemma-title }
> **補題1.3.2**
>
> グラフ$G=(V,E)$の隣接行列$A$と$\ell\in\Nat$を考える. 任意の$u,v\in V$に対し, $A^\ell(u,v)$は頂点$u$から$v$への長さ$\ell$の路の個数に等しい.
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

長さ$\ell\ge 1$に関する帰納法で示す.$\ell=1$のときは明らか.$W_\ell(u,v)$を頂点$u$から$v$への長さ$\ell$の路の個数とすると, $A^\ell = W_\ell$を示せばよい. 帰納法の仮定として$A^{\ell - 1} = W_{\ell - 1}$とする.$W_{\ell}$に関する漸化式を考える. 頂点$u$から$v$への長さ$\ell$の任意の路は, ある$w\in V$に対して$uw$間の長さ$\ell-1$の路と辺$wv$を連結させることによって得られる. 従って漸化式$W_\ell(u,v) = \sum_{w \in V} W_{\ell-1}(u,w) \cdot A(w,v)$が成り立つので, 帰納法の仮定より$W_\ell = W_{\ell-1}A = A^\ell$を得る.

</details>


## 単純ランダムウォーク

単純ランダムウォークとは、初期地点$X_0$を選び、現在いる頂点から一様ランダムな隣接点を選びそこに遷移するという確率的な操作を繰り返して得られるランダムウォークである.

{: .definition-title }
> **定義1.3.3(単純ランダムウォーク)**
> 
> グラフ$G=(V,E)$を考える. 遷移確率行列が
>
> $$
  P_{\SRW}(u,v) \defeq \begin{cases}
    \frac{1}{\deg(u)} & \text{if }\{u,v\}\in E, \\
    0                 & \text{otherwise}
  \end{cases}
> $$
>
> で与えられる$V$上のランダムウォークを$G$上の**単純ランダムウォーク (simple random walk)**という.

単純ランダムウォークの定常分布の一つは

<div id="eq:SRW_stationary_distribution" style="text-align: right;">
$$
  \pi(u) = \frac{\deg(u)}{2|E|}. \tag{1}
$$
</div>
で与えられる. 一般に単純ランダムウォークは既約性や非周期性を持つとは限らない. 既約的であることの必要十分条件はグラフ$G$が連結であることであり、非周期的であることの必要十分条件はグラフ$G$の全ての連結成分のなす誘導部分グラフが二部グラフでないことである. 実際、全ての連結成分が二部グラフでないならばそれぞれに長さ奇数の閉路$C$が存在する. 各頂点$u$について、辺$\{u,v\}$上で$u\to v \to u$という遷移を考えれば長さ$2$の閉路になっている. また、頂点$u$から奇閉路$C$に向い、$C$に沿って遷移した後に再び$u$に戻るという経路を考えればこれは奇数長の閉路である. すなわち$P^2(u,u)>0$かつある奇数$\ell$に対し$P^{\ell}(u,u)>0$となるため頂点$u$の周期は$1$である. 逆に二部グラフならば全ての閉路が偶数長なので任意の奇数$\ell$と頂点$u\in V$に対し$P^\ell(u,u)=0$である.

## 遅延単純ランダムウォーク

単純ランダムウォークは二部グラフ上では分布が収束しないという問題点があったが、これは以下のようにランダムウォークの遷移に自己ループを許容することによって解決することができる.

{: .definition-title }
> **定義1.3.4(遅延単純ランダムウォーク)**
>
> グラフ $G=(V,E)$ 上の単純ランダムウォークの遷移確率行列を $P_{\text{SRW}}$ とする. 確率行列 $P_{\text{LSRW}} \defeq \frac{1}{2}(I + P_{\text{SRW}})$ を遷移確率行列とする $V$ 上のランダムウォークを **遅延単純ランダムウォーク (lazy simple random walk)** という. ここで $I$ は単位行列.

要するに遅延単純ランダムウォークとは各頂点に確率 $1/2$ の自己ループの遷移を許したランダムウォークである. 遷移確率行列の定義より単純ランダムウォークと同じ定常分布を持つ. 自己ループの遷移を許すことによって各頂点の周期が必ず $1$ となるため、遅延単純ランダムウォークは必ず非周期的である. 従って、連結グラフ上の遅延単純ランダムウォークは[式(1)](#eq:SRW_stationary_distribution) で与えられる定常分布に一意収束する.

## グラフ上での上昇ウォークと下降ウォーク

グラフ $G=(V,E)$ 上の遅延単純ランダムウォークの1回の遷移は次の2つのステップに分解して考えることができる:

1. 現在いる頂点 $u \in V$ に接続している辺 $e \in E$ を一様ランダムに選ぶ.
2. 選んだ辺 $e$ に含まれる二頂点を一様ランダムに選び、その頂点に遷移する.

ステップ1でどの辺を選んだとしてもステップ2で確率 $1/2$ で元の頂点 $u$ に戻る. 一方でステップ2で $u$ でない方の頂点を選んだ場合は、$u$ にとって一様ランダムな隣接点に遷移したことになる. 従ってこの2ステップに基づく遷移は遅延単純ランダムウォークと同じ遷移確率行列をもつ. ステップ1を頂点 $u$ から開始したときに辺 $e$ が選ばれる確率を $\Pup_0(u,e) \in [0,1]^{V \times E}$ とし、同様にステップ2を辺 $e$ から開始したときに頂点 $w \in \{u,v\}$ が選ばれる確率を $\Pdown_1(e,w)$ とする. すなわち

$$
\begin{align*}
  & \Pup_0(u,e) = \begin{cases}
              \frac{1}{\deg(u)} & & \text{if }u \in e, \\
              0                 & & \text{otherwise}.
             \end{cases} \\
  & \Pdown_1(e,w) = \begin{cases}
                \frac{1}{2} & & \text{if }e \ni w, \\
                0           & & \text{otherwise}.
              \end{cases}
\end{align*}
$$

このとき、遅延単純ランダムウォークの遷移確率行列 $P_{\LSRW}$ は $P_{\LSRW} = \Pup_0 \Pdown_1$ と表せる.

逆に、二つのステップを入れ替え、$P' \defeq \Pdown_1 \Pup_0 \in [0,1]^{E\times E}$ を遷移確率行列としてもつ $E$ 上のランダムウォークも考えることができる. このランダムウォークの遷移は次の2ステップで与えられる:

1. 現在いる辺 $e = \{u,v\}$ に含まれる頂点を一様ランダムに選び $w \in e$ とする.
2. 選んだ頂点 $w$ に接続している辺 $e' \in E$ を一様ランダムに選び、その辺に遷移する.

このランダムウォークの遷移確率行列 $P'$ の対角成分は全て正なので非周期的である. さらに元のグラフ $G$ が連結ならば既約的である. 従って定常分布が一意に存在し、その分布への収束性が成り立つ.

## 重み付きグラフ上のランダムウォーク

単純ランダムウォークでは接続している全ての辺は同じ重みを持っている. 各辺に重みと呼ばれる正の実数を割り当てることによって、重みの大きい辺がより選ばれやすくなるようなランダムウォークを考えることができる.

{: .definition-title }
> **定義1.3.5(重み付きランダムウォーク)**
>
> グラフ$G=(V,E)$に対し、関数$w\colon E\to \Real_{> 0}$を**辺重み (edge weight)**という. 頂点$u$から$v$に遷移する確率$P(u,v)$が辺重み$w(\{u,v\})$に比例するような$V$上のランダムウォークを**重み付きランダムウォーク (weighted random walk)**と呼ぶ. すなわち、重み付きランダムウォークとは以下の遷移確率行列$P$を持つランダムウォークである:
>
> $$
> P(u,v) = \begin{cases}
> \frac{w(\{u,v\})}{\deg_w(u)} & \text{if }\{u,v\}\in E,\\
> 0 & \text{otherwise}.
> \end{cases}
> $$
>
> ここで、$\deg_w(u)=\sum_{v\colon \{u,v\}\in E} w(\{u,v\})$は頂点$u$の重み付き次数とする.

辺重み$w$を常に$1$を返す関数とすれば、$G$上の単純ランダムウォークと同一である. 自己遷移は発生しないので単純遅延ランダムウォークは表現できない. 重み付きランダムウォークの概念は後で単体複体上での局所的なランダムウォークの定義で用いる.
