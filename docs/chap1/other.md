---
title: その他の話題
nav_order: 6
parent: ランダムウォーク概論
---

# レイリー商

以下の結果は第二固有値の上界を得るときなどに役にたつ.

<div id="lemma:Rayleigh quotient" markdown="1">
{: .lemma-title }
> **補題1.6.1**
>
> 定常分布$\pi$をもつ既約的かつ可逆なランダムウォークの遷移確率行列$P$に対し, 以下が成り立つ:
> 
> $$
> \begin{align*}
> &\max_{f \in \pispace\setminus\{0\},\piprod{f,\allone}=0}\frac{\piprod{f,Pf}}{\pinorm{f}^2}=\lambda_2(P),\\
> &\min_{f \in \pispace\setminus\{0\}}\frac{\piprod{f,Pf}}{\pinorm{f}^2}=\lambda_{|V|}(P).
> \end{align*}
> $$
</div>

<div id="proof:Rayleigh quotient" markdown="1">
{: .proof-title }
<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

$|V|=n$とする.
[定理1.4.4]({{site.baseurl}}/docs/chap1/pi_innerprod#thm:eigendecomposition)の正規直交基底$x_1=\allone,x_2,\dots,x_n$を使って

$$
f = \sum_{i=1}^n f_i x_i
$$

と表す.
ここで$f_i = \piprod{f,x_i}$であり, $\piprod{f,\allone}=0$より$f_1 =0$である.
各$x_i$は固有値$\lambda_i(P)$に対応する固有ベクトルなので,

$$
\piprod{f,Pf} = \sum_{i=2}^n\lambda_i f_i^2 \le \lambda_2(P) \sum_{i=2}^n f_i^2 = \lambda_2(P) \pinorm{f}^2
$$

より最初の等号を得る.
同様に,

$$
\piprod{f,Pf} = \sum_{i=2}^n\lambda_i f_i^2 \ge \lambda_n(P) \sum_{i=2}^n f_i^2 = \lambda_n(P) \pinorm{f}^2
$$

より後半の等号も得る.

</details>
</div>

値$\frac{\piprod{f,Pf}}{\pinorm{f}^2}$を**レイリー商 (Rayleigh quotient)**と呼ぶ.
ある遷移確率行列$P$に対して$\lambda_2(P) \le \lambda$であることを示したいときには,
任意の$\allone$と直交するベクトル$f\in\pispace$に対しレイリー商が高々$\lambda$であることを示せばよい.

# 片側の固有値のバウンド

[系1.5.3]({{site.baseurl}}/docs/chap1/mixing_spectral#cor:general expander mixing lemma)は$\lambda(P)$が小さいときに二次形式$\piprod{f,g} - \Epi f \cdot \Epi g$を両側から押さえているが,
同様の証明を考えると$\lambda_2(P)$のみが小さいことが保証されている場合も同様に二次形式の片側のバウンドを得ることができる.

<div id="lemma:one side EML" markdown="1">
{: .lemma-title }
> **補題1.6.2**
>
> 任意の$f,g\in \pispace$に対し,
>
> $$
> \piprod{f,Pg} - \Epi f\cdot \Epi g \le \lambda_2(P)\sqrt{\Varpi f \cdot \Varpi g}.
> $$
</div>
