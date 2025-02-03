---
title: 応用
nav_order: 5
parent: エクスパンダーグラフ
---
# エクスパンダーグラフの応用

グラフのエクスパンダー性は組合せ論的な興味だけでなく, 理論計算機科学において多くの定理の証明の道具として非常に重要な役割を果たしている. ここではその一端を軽く紹介する. より詳細の議論は\cite{HLW06}を参照されたい.

## 脱乱択化

乱択は計算能力を真に向上させるかという問いは計算量理論において今なお重要な未解決問題であり, 暗号の計算量理論的安全性などにも応用される. この分野の中心的なリーダーの一人Avi Wigdersonは2021年にAbel賞, 2023年にTuring賞を受賞している. 興味深いことに計算量理論では「乱択計算を決定的に模倣できる」という見解が主流を占めている. すなわち, 乱択計算に用いるコイントスをなくせるというのである! ここではエクスパンダーグラフを使って乱択計算に用いるコイントスの「回数」を減らす手法\cite{AKS87}を紹介する.

本来ならば乱択計算を定義するためにチューリング機械の定義から始める必要があるのだが, それらは本講義のトピックから大きく逸脱してしまうので, ここでは大きく簡略化した次の設定を考えよう: 集合$\{0,1\}^n$の各元に$0$または$1$のどちらかの数字が割り当てられており, $1$が割り当てられたものを「あたり」とみなしたくじ引きを行う. 「あたり」の個数は少なくとも$\varepsilon\cdot 2^n$個ある. 確率$1/2$以上で「あたり」を引く方法のうち, ランダムネスをできるだけ少なくしたい.

愚直に考えると, 適当なパラメータ$k$に対し, 独立一様ランダムに$k$個の文字列$r_1,\dots,r_k\sim\binset^n$を選び, その中に「あたり」があるかどうかを確認すればよい. これらの中に「あたり」が一つ以上含まれる確率は$1-(1-\varepsilon)^k \ge 1-\exp(-k\varepsilon)$なので, 成功確率$1/2$を達成するには$k=O(1/\varepsilon)$とすればよい. 各$r_i$を選ぶにはそれぞれで$n$ビットのランダムネスを要するので, 全体で$kn = O(n/\varepsilon)$ビットのランダムネスが必要である.

{: .proposition-title }
> **命題2.5.1**
>
> $n + O\qty(1/\varepsilon)$ビットのランダムネスを用いて確率$1/2$以上で「あたり」を引く方法がある.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明の概要</summary>

頂点数$2^n$の$8$-正則$0.9$-エクスパンダーグラフ$G=(V,E)$を[定理2.2.2]({{site.baseurl}}/docs/chap2/explicit_construction#thm:Margulis_construction)を用いて決定的に構成し, 適当な全単射を用いて$V$を$\binset^n$と同一視する (ここで用いる全単射は何でもよい). あとで定まる適切なパラメータ$\ell\in\Nat$に対し, 初期頂点を一様ランダムにした$G$上の$\ell$ステップの単純ランダムウォーク $$(X_t)_{t=0,\dots,\ell}$$ を考え, 訪問した頂点$X_0,\dots,X_\ell$の中に「あたり」があるかどうかを調べる. 初期頂点の選択で$n$ビットのランダムネスを用いるが, グラフ$G$は$8$-正則グラフなのでランダムウォークの各遷移では$\log_2 8=3$ビットのランダムネスを使用する. 従って, この方法で用いるランダムネスは全体で$n + 3\ell$ビットである.

「あたり」以外の頂点からなる集合を$B$とすると, $\frac{\abs{B}}{2^n} = 1-\varepsilon$なので, $\mu = 1-\varepsilon, \lambda=0.9$として[命題2.4.4]({{site.baseurl}}/docs/chap2/property#prop:expander_walk_hitting)を適用すると, $\ell=10/\varepsilon$に対して少なくとも確率$1-(1-0.1\varepsilon)^\ell \ge 1-\e^{-1} \ge 1/2$でランダムウォークは「あたり」の頂点を一回以上は訪問する. すなわち確率$1/2$以上でこの方法は「あたり」を引く.

</details>

乱択計算の文脈では, 一回のくじ引きが乱択計算のシミュレーションに対応しており, 「あたり」を引くということはその乱択計算が正しい計算結果を出力したことを意味する. 独立なランダムネスを用いて繰り返すとその繰り返し回数に比例したランダムネスを要するが, 独立性の代わりにランダムウォークのエクスパンダー性を用いれば, 要するランダムネスの量を減らせるのである.

## 誤り訂正符号

誤り訂正符号 (error-correcting code) または単に符号 (code) とは文字列に冗長性を持たせることでノイズに対する頑健性を与える手法である. 数学的には符号はビット列の集合 $\Code\subseteq\mathbb{F}_2^n$ であり, その元 $f\in\Code$ を**符号語 (codeword)** と呼ぶ.
ここで $n$ を符号 $\Code$ の符号長 (code length) と呼ぶ.
符号には, 任意の相異なる二つの符号語が互いにハミング距離の意味で離れていることが望まれる. 形式的には, 正規化されたハミング距離 

$$
\dist(f,g)=n^{-1}\sum_{i\in[n]}\indicator{f(i)\neq g(i)}=\Pr_{i\sim[n]}[f(i)\neq g(i)]
$$

を考え, $\min_{f\neq g\in\Code}\dist(f,g)$ を符号 $\mathcal{C}$ の**距離 (distance)** という. 文字列 $f\in\Ftwo^n$ と
符号 $\Code\subseteq\Ftwo^n$ に対して $\dist(f,\Code)=\min_{w\in\Code}\dist(f,w)$ を $f$ の $\Code$ への距離とする.

符号 $\Code\subseteq\mathbb{F}_2^n$ が線形部分空間となるとき, 符号 $\Code$ を**線形符号 (linear code)** と呼ぶ. 文脈によっては線形符号のことを単に符号と呼ぶこともあり, 本講義も以降は特に断りのない限りこの慣習に従う. すなわち符号と言えばそれは線形部分空間を意味する. 符号長 $n$, ランク $k$ の線形符号に対し, $k/n$ をその符号の**レート (rate)** と呼ぶ. 直感的には符号のレートはその符号が空間 $\mathbb{F}_2^n$ 内でどれほど密に充填しているかを表すため, 符号のレートと距離にはトレードオフがある. 線形符号 $\Code$ の距離は最小ハミング重みを持つ非ゼロの符号語によって与えられることに注意されたい.

ここでは, [ケイリーグラフ]({{site.baseurl}}/docs/chap2/explicit_construction#def:Cayley_graph) を用いて構成される符号を紹介する.

{: .definition-title }
> **定義2.5.2 (ケイリーエクスパンダー符号)**
>
> ケイリーグラフ $\Cay(A,G)=(V,E)$ と符号 $\Code_A\subseteq\Ftwo^A$ を考える. 頂点 $g\in V$ と関数 $f\colon E \to \Ftwo$ に対し, $f_g=(f(\{g,ag\}))_{a\in A}\in \Ftwo^A$ と定める. 符号 $\Code_A\subseteq \Ftwo^A$ に対して
> 
> $$
> \Code(A,G,\Code_A)=\{f\in\Ftwo^E\colon \forall g\in V, f_g \in \Code_A\}
> $$
> 
> を **ケイリーエクスパンダー符号** と呼ぶ.

一般の (ケイリーグラフとは限らない) 正則エクスパンダーグラフを用いて定義されるエクスパンダー符号 (expander code) が有名だが, 定義の簡潔さを優先してあえてケイリーグラフに限定したエクスパンダー符号を紹介した. もし仮に $A$ を生成系とするケイリーグラフの列 $$(\Cay(A,G_n))_{n\in\Nat}$$ とレートと距離の良い性質をもつ一つの符号 $\Code_A$ があったとしよう. すると, この一つの符号から符号の列

$$(\Code_n)_{n\in\Nat} \defeq (\Code(A,G_n,\Code_A))_{n\in\Nat}$$

を構成できる.
さらに興味深いことに, 構成に用いたケイリーグラフがエクスパンダー性を持つならば元の符号 $\Code_A$ のレートと距離の性質を符号列 $(\Code_n)$ も受け継ぐ.

{: .lemma-title }
> **補題2.5.3**
>
> $\Code_A$ のレートが $r_A$ ならば $\Code(A,G,\Code_A)$ のレートは少なくとも $2r_A-1$ である.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
符号 $\Code_A\subseteq\Ftwo^A$ のレートが $r_A$ なので, その任意の符号語 $f_0\in \Code_A$ は $|A|(1-r_A)$ 個の線形制約を満たす. ケイリーエクスパンダー符号 $\Code(A,G,\Code_A)$ の符号語 $f$ は, 全ての頂点 $g\in G$ に対して $f_g$ が $\abs{A}(1-r_A)$ 個の線形制約を満たしているので, $f$ は高々 $|G||A|(1-r_A)$ 個の線形制約を満たしている. つまり $f$ の自由度は少なくとも $|E|-|G||A|(1-r_A)=|E|(1-2(1-r_A))$ なので, $\Code(A,G,\Code_A)$ のレートは少なくとも $1-2(1-r_A)=2r_A-1$ となる.
</details>

<div id="lem:expander_code_distance" markdown="1">
{: .lemma-title }
> **補題2.5.4**
>
> 符号 $\Code_A$ の距離が $\delta_A$, ケイリーグラフ $\Cay(A,G)$ が $\lambda$-エクスパンダーならば, ケイリーエクスパンダー符号 $\Code(A,G,\Code_A)$ の距離は少なくとも $\delta_A(\delta_A-\lambda)$ である.
</div>

証明にはエクスパンダー混交補題からすぐに従う以下の系を用いる:

<div id="cor:EML" markdown="1">
{: .corollary-title }
> **系2.5.5**
>
> $d$-正則な $\lambda$-エクスパンダー $G=(V,E)$ の頂点部分集合 $S\subseteq V$ が $e(S,S)\geq cd\abs{S}$ を満たす (言い換えると, 誘導部分グラフ $G[S]$ の平均次数が $cd$ 以上) ならば, $\abs{S}\geq (c-\lambda)n$ を満たす.
</div>

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
$S=T$として[補題2.4.2]({{site.baseurl}}/docs/chap2/property#lem:expander_mixing_lemma)を適用すると

$$
\begin{align*}
    cd\abs{S} \leq e(S,S) \leq \frac{d}{\abs{V}}\abs{S}^2+\lambda d \abs{S}.
\end{align*}
$$

これを解くと$\abs{S}\geq (c-\lambda)n$を得る.
</details>

これを使って[補題2.5.4](#lem:expander_code_distance)の証明を与える.
<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">補題2.5.4の証明</summary>
任意の非ゼロの符号語 $f\in\Code(A,G,\Code_A)$ が少なくとも $\delta_A(\delta_A-\lambda)\abs{E}$ 個の $1$ を持つことを言えばよい. 符号語 $f\neq 0$ に対し, $F=\set{e\in E\colon f(e)=1}$ とし, $S=\bigcup_{e\in F}e$ を $F$ の辺と接続している頂点の全体とする (辺 $e$ を要素数 $2$ の頂点部分集合として見ている). $\abs{F}\geq\delta_A(\delta_A-\lambda)\abs{E}$ を示せばよい.

$\Code_A$ の距離の条件より, 各 $g\in S$ に対して $f_g\in\Ftwo^A$ は少なくとも $\delta_A\abs{A}$ 本の辺が接続している. すなわち, $\Cay(A,G)$ の部分グラフ $(S,F)$ の最小次数は $\delta_A\abs{A}$ を満たすので $\abs{F}\geq \frac{\delta_A \abs{A}}{2}\abs{S}$. 誘導部分グラフ $G[S]$ は $(S,F)$ を部分グラフとして含むので $e(S,S)\geq 2\abs{F}$. さらに, $(S,F)$ に対する握手補題より

$$
\begin{align*}
    e(S,S)\geq 2\abs{F}\geq \delta_A\abs{A}\abs{S}.
\end{align*}
$$

[系2.5.5](#cor:EML)
より $\abs{S}\geq (\delta_A-\lambda)\abs{G}$ なので, $\abs{F}\geq \frac{\delta_A\abs{A}}{2}\abs{S}\geq \delta_A(\delta_A-\lambda)\frac{\abs{G}\abs{A}}{2}=\delta_A(\delta_A-\lambda)\abs{E}$ を得る.
</details>

{: .lemma-title }
> **補題2.5.6**
>
> 符号 $\Code_A$ の距離が $\delta_A$, ケイリーグラフ $\Cay(A,G)$ が $\lambda$-エクスパンダーならば, ケイリーエクスパンダー符号 $\Code(A,G,\Code_A)$ の距離は少なくとも $\delta_A(\delta_A-\lambda)$ である.

<details markdown="1" style="background-color: #eee;">
<summary style="display: list-item">証明</summary>
任意の非ゼロの符号語 $f\in\Code(A,G,\Code_A)$ が少なくとも $\delta_A(\delta_A-\lambda)\abs{E}$ 個の $1$ を持つことを言えばよい.
符号語 $f\neq 0$ に対し, $F=\set{e\in E\colon f(e)=1}$ とし, $S=\bigcup_{e\in F}e$ を $F$ の辺と接続している頂点の全体とする (辺 $e$ を要素数 $2$ の頂点部分集合として見ている).
$\abs{F}\geq\delta_A(\delta_A-\lambda)\abs{E}$ を示せばよい.

$\Code_A$ の距離の条件より,
各 $g\in S$ に対して $f_g\in\Ftwo^A$ は少なくとも $\delta_A\abs{A}$ 本の辺が接続している.
すなわち, $\Cay(A,G)$ の部分グラフ $(S,F)$ の最小次数は $\delta_A\abs{A}$ を満たすので $\abs{F}\geq \frac{\delta_A \abs{A}}{2}\abs{S}$.
誘導部分グラフ $G[S]$ は $(S,F)$ を部分グラフとして含むので $e(S,S)\geq 2\abs{F}$.
さらに, $(S,F)$ に対する握手補題より

$$
\begin{align*}
    e(S,S)\geq 2\abs{F}\geq \delta_A\abs{A}\abs{S}.
\end{align*}
$$

[系2.5.5](#cor:EML)より $\abs{S}\geq (\delta_A-\lambda)\abs{G}$ なので,
$\abs{F}\geq \frac{\delta_A\abs{A}}{2}\abs{S}\geq \delta_A(\delta_A-\lambda)\frac{\abs{G}\abs{A}}{2}=\delta_A(\delta_A-\lambda)\abs{E}$ を得る.
</details>
