---
title: 定義
nav_order: 1
parent: マトロイド
---

# マトロイドの定義

ある性質を持つ単体複体のことをマトロイドといいます.

{: .definition-title }
> **定義4.1.1(マトロイド)**
>
> 次の性質を持つ単体複体$(V,\F)$を**マトロイド (matroid)**という:
> 任意の$\sigma,\tau \in \F$に対し, $\abs{\sigma} < \abs{\tau}$ならば,
> ある$u \in \tau \setminus \sigma$が存在して
>
> $$\sigma \cup \{u\} \in \F.$$
> 
> マトロイド$(V,\F)$の面$\sigma\in \F$を特に**独立集合 (independent set)**という.

{: .definition-title }
> **定義4.1.2(基)**
>
> マトロイドの(包含関係に関して)極大な独立集合を**基 (basis)**といい, 基全体の集合を$\B$で表す.

マトロイドは純粋な単体複体です.
実際, もし$\abs{B} < \abs{B'}$なる二つの基$B,B'\in\B$が存在するならば,
マトロイドの定義より,
ある$u \in B'\setminus B$が存在して$B\cup \{u\} \in \F$とできるが,
これは$B$の極大性に矛盾する.

特に断りのない限り, 基上の[定常分布]({{site.baseurl}}/docs/chap3/global#def:down_walk_and_stationary_distribution)は一様分布とします.

### 例1. 一様マトロイド
[単体複体の例2]({{site.baseurl}}/docs/chap3/definition#例2)で定まる単体複体$\qty(V,\binom{V}{\le k})$は**一様マトロイド (uniform matroid)**と呼ばれるマトロイドである.

### 例2. グラフ的マトロイド
[単体複体の例3]({{site.baseurl}}/docs/chap3/definition#例3)で定まる単体複体$(V,\F)$はマトロイドです.
ここでは証明の概要を説明する.
マトロイドであることを示すには, 任意の二つの森$\sigma,\tau \in \F,\abs{\sigma} < \abs{\tau}$に対して, ある辺$e\in \tau\setminus \sigma$が存在して$\sigma\cup\{e\}$が閉路を含まないようにできることを言えばよい.
二つの森$\sigma,\tau \in \F,\abs{\sigma} < \abs{\tau}$を固定する.
森$\sigma\in \F$はグラフ上で複数の連結成分をなす.
これら連結成分の個数は$|V| - \abs{\sigma}$に等しい.
さて, 森$\tau$の中には, $\sigma$のなす連結成分のうち相異なる二つの間を横切る辺$e \in \tau \setminus \sigma$が存在する (下図参照).
そうでなければ, $\tau$のなす連結成分の個数$|V|-\abs{\tau}$は$|V|-\abs{\sigma}$以下となってしまい, $\abs{\tau} > \abs{\sigma}$に矛盾.
この辺$e$を$\sigma$に追加しても閉路は発生しない.
(もし閉路$C$が生じるならば, $e$が$\sigma$のなす連結成分を横切ることに矛盾する).
すなわち, $\sigma\cup\{e\}\in\F$であり, 確かに$(V,\F)$はマトロイドである.

{: align="center"}
![text]({{site.baseurl}}/docs/images/graphicmatroid.png){: width="40%" }

{: align="center"}
<span style="font-size: smaller;">森$\sigma$のなす連結成分をまたがる辺$e \in \tau$が必ず存在する.</span>

グラフの森から定まる上記のマトロイドは**グラフ的マトロイド (graphic matroid)**と呼ばれるマトロイドの重要なクラスをなす.

### 例3. 線形マトロイド
[単体複体の例4]({{site.baseurl}}/docs/chap3/definition#例4)で定まる単体複体$(V,\F)$は**線形マトロイド (linear matroid)**と呼ばれるマトロイドである.
$\sigma,\tau\in \F$であって$\abs{\sigma} < \abs{\tau}$であるとする.
全てのベクトル$x\in \tau$が$x\in \mathrm{span}(\sigma)$に属するならば, $\tau$の線型独立性に矛盾するのであるベクトル$x\in \tau$が存在して$\{x\}\cup\sigma\in\F$となる.

### 例4. 分割マトロイド
有限集合$V$の分割$V=W_1\sqcup \dots \sqcup W_k$と非負整数$d_1,\dots,d_k\ge 0$を固定する.
部分集合族$\F$を

$$
    F \in \F \iff \forall i\in\{1,\dots,k\},\abs{W \cap W_i} \le d_i     \label{eq:partition matroid}
$$

で定義したとき, $(V,\F)$は**分割マトロイド (partition matroid)**と呼ばれるマトロイドである.
平たく言えば, 各$W_i$の元を高々$d_i$個ずつ含むものからなる部分集合族である.

### マトロイドでない例
クリーク複体やマッチング全体のなす単体複体はそもそも純粋とは限らないので必ずしもマトロイドになるとは限らない.
