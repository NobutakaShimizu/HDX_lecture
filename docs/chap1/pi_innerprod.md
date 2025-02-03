---
title: 定常分布から定まる内積とノルム
nav_order: 5
parent: ランダムウォーク概論
---
# 定常分布から定まる内積とノルム

可逆なランダムウォークは遷移確率行列の固有値を考える上で非常に扱いやすいランダムウォークのクラスとなっている. ランダムウォークの分布は遷移確率$P$を右から掛けて得られるのに対し, 固有値に基づく議論では左固有値を考えており, この左右の差異に違和感を覚える読者もいるであろう. 実は可逆なランダムウォークでは遷移確率行列を対称行列のように扱うことができ, ゆえに左右どちらから作用させようが本質的に同じとなる. このことを説明するために, $\Real^V$に次の内積を導入する.

<div id="def:naiseki" markdown="1">
{: .definition-title }
> **定義1.5.1**
>
> 有限集合$V$上の分布$\pi\in(0,1]^V$に対し,
> $\Real^V$に以下の内積$\piprod{\cdot,\cdot}$を定めた内積空間を$\pispace$で表す:
>
> $$
 \begin{align*}
  \piprod{f,g} \defeq \sum_{u \in V} \pi(u) f(u) g(u)
  = f^\top \Pi g.
 \end{align*}
> $$ 
>
> ここで$f,g$は列ベクトルとして扱い, $\Pi=\mathrm{diag}(\pi)$はベクトル$\pi$の成分を対角に並べた行列である.
> また, 内積$\piprod{\cdot,\cdot}$が誘導するノルムを$\pinorm{\cdot}$で表す.
> すなわち, $f\in\Real^V$に対して
>
> $$
  \pinorm{f} \defeq \sqrt{\piprod{f,f}}.
> $$
</div>

[定義1.5.1](#def:naiseki)で考える分布$\pi$は全ての成分が正であるため,
上記の内積$\piprod{\cdot,\cdot}$はちゃんと実ベクトル空間の内積の公理(対称双線形性, 非退化性, 半正定値性)を満たしており,
確かに$\pispace$は内積空間である.

$\Real^V$上の通常の内積$\inprod{\cdot,\cdot}$を考えたとき, 任意の対称行列$M \in \Real^{V\times V}$とベクトル$f,g\in \Real^V$に対して $\inprod{f,Ag} = \inprod{Af,g}$
が成り立っていたが,
可逆なランダムウォークの遷移確率行列$P$は内積$\piprod{\cdot,\cdot}$に関して同様の性質を持つ.

<div id="lemma:reversible_adjoint" markdown="1">
{: .lemma-title }
> **補題1.5.2**
>
> 定常分布$\pi$をもつ既約的かつ可逆なランダムウォークの遷移確率行列$P$は,
> 任意の$f,g\in\Real^V$に対して
>
> $$
  \piprod{f,Pg} = \piprod{Pf,g}
> $$
>
> を満たす.

[補題1.5.2](#lemma:reversible_adjoint)は内積$\piprod{\cdot,\cdot}$に関して遷移確率行列$P$が随伴行列となることを示している.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
  
  定常分布$\pi$を対角成分に並べた対角行列$\Pi$を考えると

  $$
  \begin{align*}
    \piprod{f,Pg} & = f^\top \Pi P g                                              \\
          & = f^\top (\Pi P)^\top g &  & \text{$\because$可逆性より$\Pi P$は対称} \\
          & = (Pf)^\top \Pi g       &  & \text{$\because\Pi^\top = \Pi$}  \\
          & = \piprod{Pf,g}.
  \end{align*}
  $$

</details>

一般に$P$が可逆とは限らない場合, 時間反転ランダムウォークの遷移確率行列$P^*$に対し

$$ \piprod{f,Pg} = \piprod{P^*f,g} $$

が成り立つ. この意味で$P^*$は$P$の随伴とみなすことができる.

対称行列に対して展開される固有値分解などの理論は可逆なランダムウォークの遷移確率行列に対しても同様に展開できる.
例えば, 対称行列と同様に可逆なランダムウォークの遷移確率行列は実固有値をもつ.

<div id="lemma:reversible_real_eigenvalue" markdown="1">
{: .lemma-title }
> **補題1.5.3**
>
> 既約的かつ可逆なランダムウォークの遷移確率行列$P$と定常分布$\pi$に対し,
> 行列
>
> $$
> \begin{align}
>     A \defeq \sqrt{\Pi} P \sqrt{\Pi}^{-1} \tag{1}\label{eq: symmetrized P}
> \end{align}
> $$
>
> を考える.
> $P$と$A$は(多重度も含め)同じ固有値をもち, これらは全て実数である.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

行列$A$は対称である.
実際,
$$
\begin{align*}
  A^\top & = \sqrt{\Pi}^{-1} P^{\top} \sqrt{\Pi}                            &  & \text{$\because\sqrt{\Pi},\sqrt{\Pi}^{-1}$は対称} \\
     & = \sqrt{\Pi} \cdot \Pi^{-1} P^{\top} \Pi \cdot \sqrt{\Pi}^{-1}                                                         \\
     & = \sqrt{\Pi} \cdot \Pi^{-1} (\Pi P)^{\top} \cdot \sqrt{\Pi}^{-1}                                                       \\
     & = \sqrt{\Pi} \cdot \Pi^{-1} \Pi P \cdot \sqrt{\Pi}^{-1}          &  & \text{$\because$可逆性より$\Pi P$は対称}                 \\
     & = A.
\end{align*}
$$

$A$は対称なので全ての固有値は実数である.

$A$と$P$は相似なので多重度も含めて同じ固有値をもつ. 実際,
$A$の固有値$\lambda$に対する固有ベクトルを$x$とし, ベクトル$y\defeq \sqrt{\Pi}^{-1}x$を考える.
固有ベクトルの式

$$
\begin{align*}
  A x = (\sqrt{\Pi} P \sqrt{\Pi}^{-1})x =  \lambda x
\end{align*}
$$

の両辺に左から$\sqrt{\Pi}^{-1}$を掛けると

$$
\begin{align*}
  P y = \lambda y
\end{align*}
$$

を得る.
すなわち, $P$と$A$は同じ固有値を持つ.
特に, $P$の固有値も全て実数である.
