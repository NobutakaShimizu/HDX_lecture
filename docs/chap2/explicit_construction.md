---
title: 陽な構成
nav_order: 2
parent: エクスパンダーグラフ
---

# 陽な構成
エクスパンダー性はランダムウォークがすぐに混ざり合うということを意味し, これを満たすグラフは多くの辺を持つべきである.
例えば完全グラフは非常に強いエクスパンダー性を持つ一方で閉路グラフのエクスパンダー性は乏しい.
では, 疎でありかつエクスパンダー性をもつグラフは存在するだろうか?
また, 陽に構成できるだろうか?

## ランダム正則グラフ

$n$頂点$d$-正則グラフ全体の集合を$\calG_{n,d}$とし、$\calG_{n,d}$から一様ランダムに選ばれたグラフ$G\sim\calG_{n,d}$を考える（$nd$は常に偶数とする）。この確率変数をランダム正則グラフという。ランダム正則グラフは「最適な」エクスパンダーグラフであることが知られている\cite{Friedman_random_regular}。

{: .theorem-title }
> **定理2.2.1 (Friedmanの定理)**
>
> 任意の$d\ge 3$と任意の$\varepsilon > 0$に対し、
>
> $$
> \lim_{n\to\infty}\Pr\qty[\lambda(P) \ge \frac{2\sqrt{d-1}}{d} + \varepsilon] = 0.
> $$


## Margulisの構成

先の節ではランダムな正則グラフがエクスパンダーになることを見てきたが, 陽に構成できるエクスパンダーグラフも存在する.
定数$\lambda<1$に対し$\lambda$-エクスパンダーの族は\citet{Margulis1973}によって初めて与えられ,
そのスペクトルギャップの陽な値は\citet{GG81}により初めて与えられた.
より詳細な背景や定理の証明は\cite{HLW06}を参照されたい.

<div id="thm:Margulis_construction" markdown="1">
{: .theorem-title }
> **定理2.2.2(Margulisの構成)**
>
> グラフ族 $(G_m)_{m\in\Nat}$ を以下で定義する:
> 頂点集合 $V_m = \mathbb{Z}_m \times \mathbb{Z}_m$ とし,
>
> $$
  \begin{align*}
      T_1 = \begin{bmatrix}
          1 & 2 \\
          0 & 1
      \end{bmatrix},& &
      T_2 = \begin{bmatrix}
          1 & 0 \\
          2 & 1
      \end{bmatrix},& &
      e_1 = \begin{bmatrix}
          1 \\
          0
      \end{bmatrix}, & &
      e_2 = \begin{bmatrix}
          0 \\
          1
      \end{bmatrix}
  \end{align*}
> $$
>
> とする.
> 各頂点$v=(x,y)\in V_m$を
> 
> $$
> T_1v,\quad T_2v,\quad T_1v+e_1,\quad T_2v+e_2
> $$
> 
> およびこれらの逆変換で与えられる八つの頂点と接続させて得られるグラフを$G_m$とする (多重辺や自己ループも含みうる).
> このとき, 任意の$m\in\Nat$に対して$\lambda(G_m) \le \frac{5\sqrt{2}}{8} < 0.9$.
</div>

## ケイリーグラフ
エクスパンダーグラフを陽に構成する最も重要なアプローチの一つとしてケイリーグラフ\cite{Cayley1878}と呼ばれる概念が知られている。

<div id="def:Cayley_graph" markdown="1">
{: .definition-title }
> **定義2.2.3 (ケイリーグラフ)**
>
> $G$を有限群, $A\subseteq G$を$G$の生成系であって単位元を含まず, 逆元で閉じているとする.
> 頂点集合$V=G$, 辺集合$E=\set{\set{g,ag}\colon g\in G,a\in A}$に対し$(V,E)$で与えられるグラフを**ケイリーグラフ (Cayley graph)** といい, $\Cay(A,G)$で表す。
> 頂点$g\in G$に対し, $E_g=\set{\set{g,ag}\colon a\in A}$を$g$を含む辺の集合とする。
</div>

ケイリーグラフは群の幾何学的な性質を調べる幾何学的群論における重要な研究対象の一つである。$A$は単位元を含まないため自己ループは存在しない。また, $A^{-1}=A$より$\set{ag,a^{-1}(ag)}\in E$となるため$\Cay(A,G)$は無向グラフとなっている。同様にケイリーグラフ$\Cay(G,A)$も考えることができるが, 写像$x\mapsto x^{-1}$を考えると$\Cay(A,G)$と$\Cay(G,A)$が同型になっているので本質的には同じである。ケイリーグラフ$\Cay(A,G)$は$\abs{A}$-正則グラフである。
