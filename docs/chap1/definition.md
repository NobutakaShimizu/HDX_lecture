---
title: ランダムウォークの定義
nav_order: 1
parent: ランダムウォーク概論
---
# ランダムウォークの定義

{: .definition-title }
> **定義1.1.1(ランダムウォーク)**
> 
> 有限集合$V$と確率行列 $P\in[0,1]^{V\times V}$ に対し, $V$ 上に値をとる確率変数列 $$(X_t)_{t\ge 0}$$ であって, 任意の $t\ge 0$, 頂点列 $(v_0,\dots,v_{t-1})\in V^t$, および$v\in V$に対して
>
> $$
\begin{align*}
  \Pr\qty[X_t = v \condition X_0 = v_0,\dots,X_{t-1} = v_{t-1}] = \Pr\qty[X_t = v \condition X_{t-1} = u] = P(u,v)
\end{align*}
> $$
>
> を満たすものを$V$上の**ランダムウォーク (random walk)**という. 特に確率行列$P$をランダムウォーク$(X_t)_{t\ge 0}$の**遷移確率行列 (transition matrix)**と呼ぶ. 

初期地点$X_0$もまた確率変数であるためランダムに決まることに注意されたい. また, 決定的に$X_0=u$からスタートしていても良い. 

初期頂点$X_0$の分布が決まれば各時刻$t$における$X_t$の分布は一意に定まる. 実際, $t\ge 0$に対し$p_t \in [0,1]^{V}$を$X_t$の分布とする (すなわち, $p_t(u) = \Pr\qty[X_t = u]$). 任意の$t\ge 1$に対し

$$
\begin{align*}
  p_t(v) & = \Pr\qty[X_t = v]                                                        \\
         & = \sum_{u\in V}\Pr\qty[ X_t = v \tand X_{t-1} = u]                          \\
         & = \sum_{u\in V}\Pr\qty[ X_t = v \condition X_{t-1} = u] \Pr\qty[X_{t-1} = u] \\
         & = \sum_{u\in V} P(u,v) p_{t-1}(u)
\end{align*}
$$

という漸化式を得る. これは$p_{t} = p_{t-1} P$とも表せる (ここで$p_t$は行ベクトルとして扱う) ので

$$
\begin{align}
  p_t = p_0 P^t \label{eq:p_t}
\end{align}
$$

を得る. 

厳密には初期分布$X_0$と遷移確率行列$P$を定めないとランダムウォークは一意に定まらないが, しばし遷移確率行列$P$だけを指定して「$P$に従うランダムウォーク」という言い回しをする. このとき, 暗に初期分布$X_0$は任意の分布を考えており, 例えば「$P$に従うランダムウォークは性質$\mathcal{P}$を満たす」と言ったときは「遷移確率行列が$P$で与えられた任意のランダムウォークは性質$\mathcal{P}$を満たす」ということを意味する. 

