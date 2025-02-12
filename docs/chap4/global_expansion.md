---
title: 大域エクスパンダー性
nav_order: 4
parent: マトロイド
---

# Anari, Liu, Gharan, Vinzantの定理

<div title="thm:ALGV" markdown="1">
{: .theorem-title }
> **定理4.4.1 (Anari-Liu-Gharan-Vinzantの定理)**
>
> 任意のマトロイドは,
>
> $$
> \lambda_i = 1-\frac{1}{i+1}
> $$
>
> に対して大域$(\lambda_0,\dots,\lambda_d)$-エクスパンダーである.
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
    
次元$d$のマトロイド$X=(V,\F)$の独立集合$\sigma \in X(d-2)$を任意に固定し, リンク$X_\sigma$の$1$-スケルトン$G_\sigma$を考える. 基$\B$上の定常分布は一様分布なので, $\sigma$に関する局所ランダムウォークは$G_\sigma$上の単純ランダムウォークとなる. さて, $G_\sigma$の頂点集合$V_\sigma$は

$$
V_\sigma = \{v\in V\setminus\sigma\colon \sigma\cup \{v\} \in \F\}
$$

であり, 辺集合$E_\sigma \subseteq \binom{V_\sigma}{2}$は,

$$
E_\sigma = \set{ \{u,v\}\colon \sigma\cup\{u,v\}\in \F }
$$

となる.

ここで, 以下の主張を証明する:

$$
\{u,v\},\{v,w\}\not\in E_\sigma \Rightarrow \{u,w\} \not\in E_\sigma \tag{1}\label{eq:hogurahu_clique}
$$

これは言い換えると$G_\sigma$の補グラフの全ての連結成分はクリークであることを意味する. 主張(\ref{eq:hogurahu_clique})を背理法で証明する.
ある$\set{u,v},\set{v,w}\not\in E_\sigma$が存在して, さらに$\set{u,w}\in E$が成り立つと仮定する. このとき, $\tau\defeq \sigma\cup\set{u,w}\in \F$である. さらに, $v$は$G_\sigma$の頂点なので$\tau'\defeq \sigma\cup\set{v} \in \F$である. すなわち, $\tau,\tau'$は$\abs{\tau'} < \abs{\tau}$を満たす二つの独立集合なので, マトロイドの定義よりある$t \in \tau \setminus \tau' = \set{u,w}$に対して$\tau'\cup \set{t}=\sigma\cup\set{u,t} \in \F$, すなわち$\set{u,t}\in E_\sigma$となるが, これは$\set{u,v},\set{v,w}\not\in E$に矛盾する.

主張(\ref{eq:hogurahu_clique})より$G_\sigma$の補グラフの全ての連結成分はクリークである. これらを$C_1,\dots,C_\ell \subseteq V_\sigma$とし, $v_i\in \Real^{V_\sigma}$をクリーク$C_i$の指示ベクトルとする. $J\in\Real^{V_\sigma\times V_\sigma}$を全成分が$1$の行列とすると, $G_\sigma$の隣接行列$A\in\Real^{V_\sigma\times V_\sigma}$は

$$ A = J - \sum_{i=1}^\ell v_i v_i^\top $$

となる. さらに, 局所ランダムウォークの定常分布$\pi^\sigma_0$を対角に並べた対角行列を$\Pi$とすると, 遷移確率行列は$P_\sigma = \Pi A = \Pi J - \sum_{i=1}^\ell \Pi v_iv_i^\top$となる. 従って, 任意の$\iprod{V_\sigma}{f,\allone}=0$を満たす$f\in \ispace{V_\sigma}$に対して

$$
\iprod{V_\sigma}{f,P_\sigma f} = \iprod{V_\sigma}{f,\Pi J f} - \sum_{i=1}^\ell \iprod{V_\sigma}{f,\Pi v_iv_i^\top f} = - \sum_{i=1}^\ell \iprod{V_\sigma}{f,\Pi v_iv_i^\top f} \le 0.
$$

最後の不等式では行列$\Pi v_iv_i^\top$が半正定値性を使った. これは, $\Pi v_i v_i^\top$がランク$1$行列であるため第二以降の固有値は全て$0$に等しく, さらに第一固有値はそのトレース$\mathrm{tr}(\Pi v_i v_i^\top) = \sum_{u\in V_\sigma} \pi^\sigma_0(u) v_i(u)^2\ge 0$に等しいことから従う.

また, 全ての独立集合$\sigma\in \F$に対してリンク$X_\sigma$の$1$-スケルトン$G_\sigma$は連結である (証明は演習問題とする).

以上より, 
[トリクルダウン定理]({{site.baseurl}}/docs/chap4/local_expansion#thm:Oppenheim_trickle-down_theorem)
からマトロイド$X$は局所$0$-エクスパンダーであり, さらに$\gamma=0として
[Kaufman-Oppenheimの定理]({{site.baseurl}}/docs/chap3/local_global#thm:Kaufman-Oppenheim_theorem)
を適用すると主張を得る.

</details>

{: .corollary-title }
> **系4.4.2**
>
> 次元$d$の任意のマトロイド$(V,\F)$上の基交換ウォークの混交時間は
>
> $$ \tmix(\varepsilon) = (d+1)|V|\log\qty(\frac{1}{\varepsilon}). $$

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>

[定理4.4.1](#thm:ALGV)および$\PDU_d$の半正定値性より$\lambda(\PDU_d) \le 1-\frac{1}{d+1}$ であり, $\PDU_d$のスペクトルギャップは少なくとも$\frac{1}{d+1}$
である. また, 基上の定常分布$\pi=\pi_d$は基上の一様分布であり, 特に$\pimin \ge 1/2^{|V|}$が成り立つので, [補題1.6.4]({{site.baseurl}}/docs/chap1/mixing_spectral#lem:mixing_time_and_spectral_gap)より,

$$
 \tmix(\varepsilon) \le \frac{\log\\qty(\frac{1}{2\pimin\varepsilon})}{\log(1/\lambda(P))} \le (d+1)|V|\log\qty(\frac{1}{\varepsilon}).
$$

</details>