---
title: 局所大域原理
nav_order: 4
parent: 高次元エクスパンダー概論
---

# 単体複体の局所大域原理
単体複体における局所大域原理, すなわち, 局所エクスパンダー性は大域エクスパンダー性を導くという結果は比較的最近, **\citet{KO20}**によって証明された.

<div id="thm:Kaufman-Oppenheim_theorem" markdown="1">
{: .theorem-title }
> **定理3.4.1(Kaufman--Oppenheimの定理)**
>
> 純粋な$d$-次元単体複体$X = (V,\F)$が局所$\gamma$-エクスパンダーならば, 
>
>$$
\lambda_i = 1-\frac{1}{i+1} + \frac{\gamma i}{2}
>$$
>
> で定義された$\lambda_i$ ($i=0,\dots,d$) に対して$X$は大域$(\lambda_0,\dots,\lambda_{d})$-エクスパンダーである.
</div>

本節では[定理3.4.1](#thm:Kaufman-Oppenheim_theorem)の証明を紹介する.

## 非遅延上昇下降ウォーク
[定理3.4.1](#thm:Kaufman-Oppenheim_theorem)は, 各次元において$\PUD_i$と$\PDU_i$の固有値を比較することによって得られる. $\PDU_i$と$\PUD_{i-1}$は随伴の関係にあるため非ゼロ固有値は一致する. 一方で, $\PUD_i$と$\PDU_i$は自己ループの影響もあり, その固有値を比較するのは難しい. そこでまず, 上昇下降ウォーク$\PUD_i$から自己ループの遷移を除去したウォーク$\nonlazyPUD_i$を考え, $\nonlazyPUD_i$と$\PDU_i$の固有値を比較する.

{: .definition-title }
> **定義3.4.2(非遅延上昇下降ウォーク)**


**nonlazy updown**: **\cref{def:down walk and stationary distribution}**, **\ref{def:up walk}**と同じ設定において, 確率行列$\nonlazyPUD_i \in [0,1]^{X(i) \times X(i)}$を
\[ \nonlazyPUD_i = \frac{i+2}{i+1}\rbra*{ \PUD_i - \frac{1}{i+2}I } \]
とする. ここで$I$は$X(i)\times X(i)$の単位行列である.
**\cref{lem:PUD seibun}**より$\PUD_i$に従うランダムウォークは確率$\frac{1}{i+2}$の自己ループを持つ. 従って$\PUD_i$から$\frac{1}{i+2}I$を引くと自己ループの確率は$0$になる. しかしこうすると行和が$1-\frac{1}{i+2} = \frac{i+1}{i+2}$になるので, $\frac{i+2}{i+1}$倍して確率行列になるよう正規化したものが$\nonlazyPUD_i$である. 例えばグラフ上の単純遅延ランダムウォーク(**\cref{def:lazy SRW}**)に対して同様の操作を行うと単純ランダムウォーク(**\cref{def:SRW}**)を得る. すなわち, グラフ$G$を$1$次元単体複体とみなしたときの$\nonlazyPUD_0$は$G$上の単純ランダムウォークと等しい.
#### $\nonlazyPUD_i(\sigma,\cdot)$のサンプリング
**nonlazyUPD sampling**: **\cref{lem:PUD seibun}**, **lem:local RW seibun**より, 各成分は以下のように表せる:
\[
    \nonlazyPUD_i(\sigma,\sigma') = \begin{cases}
        \frac{1}{i+1}P_{\sigma\cap \sigma'}(\sigma\setminus\sigma',\sigma'\setminus\sigma)	& \tif \sigma\cup\sigma'\in X(i+1),\\
        0 & \totherwise.
    \end{cases}
\]
(ここでは$\sigma\setminus\sigma'$と$\sigma'\setminus\sigma$を頂点として扱っている). 従って, 分布$\nonlazyPUD_i(\sigma,\cdot)$は以下のようにして生成できる: まず, 頂点$u \sim \sigma$を一様ランダムに選び, $\rho = \sigma\setminus\{u\}$とする. 次に$v\sim P_\rho(u,\cdot)$に従って選び, $\rho\cup\{v\}$を出力する. 実際, このようにして得られたランダムな面$\rho\cup\{v\}$は, $\sigma\cup\sigma'\in X(i+1)$なる$\sigma'$に対して以下が成り立つ:
\[
    \Pr\sbra*{\rho\cup\{v\} = \sigma'} &= \Pr\sbra*{ \rho = \sigma\cap \sigma' \tand v=\sigma'\setminus\sigma } \\
    &= \frac{1}{i+1}\cdot P_{\rho}(\sigma\setminus\sigma',\sigma'\setminus\sigma).
\]
また, 面$\emptyset$上の局所ランダムウォークの遷移確率行列$P_\emptyset$と$\nonlazyPUD_0$は一致する.

### ランダムウォークの分解
非遅延上昇下降ウォーク$\nonlazyPUD_i$と下降上昇ウォーク$\PDU_i$の固有値を比較するために, これら二つのランダムウォークから得られる二次形式を局所ランダムウォークの二次形式に分解する.
#### 
**restriction**: $f\in \ispace$と面$\sigma\in X(i-1)$に対し, $f_\sigma\colon X_\sigma(0) \to \Real$を以下で定める:
\[
    f_\sigma (u) = f(\sigma\cup\{u\}).
\]
$\ispace$上の「大域的な」二次形式が各リンク$X_\sigma$上の「局所的な」二次形式の線形和で表せることを示す.
#### 
**nonlazyUP decomposition**: 純粋な$d$次元単体複体$X$と任意の$0 \le i\le d-1,f,g \in \ispace$に対し
\[ \iprod{f, \nonlazyPUD_i g} = \E_{\rho\sim X(i-1)}\sbra*{ \iprod[X_\rho(0)]{f_\rho, P_\rho g_\rho} }. \]
**\cref{rem:nonlazyUPD sampling}**を用いて以下のように左辺を式変形していくと主張を得る:
\[
    (\text{左辺}) &= \E_{\substack{\sigma\sim X(i) \\ \sigma'\sim \nonlazyPUD_i(\sigma,\cdot)}}\sbra*{ f(\sigma) g(\sigma')} \\
    &= \E_{\substack{\sigma\sim X(i)\\ u\sim \sigma,\\ \rho=\sigma\setminus\{u\} \\ v\sim P_\rho(u,\cdot)}}\sbra*{ f(\rho\cup\{u\}) g(\rho\cup\{v\}) } & & \text{$\because$\cref{rem:nonlazyUPD sampling} ($\sigma'=\rho\cup\{v\}$に対応)}\\
    &= \E_{\rho \sim X(i-1)}\sbra*{ \E_{\substack{ \sigma \sim X(i) \text{ conditioned on }\sigma\supseteq \rho \\ \{u\} = \sigma\setminus \rho \\ v \sim P_\rho(u,\cdot)}} \sbra*{ f_\rho(u) g_\rho(v) } } \\
    &=  \E_{\rho \sim X(i-1)}\sbra*{ \E_{\substack{u\sim X_\rho(0) \\ v \sim P_\rho(u,\cdot)}}\sbra*{f_\rho(u)g_\rho(v)}} & & \text{$\because$\cref{eq:pi alpha j}}\\
    &= (\text{右辺}).
\]
下降上昇ウォークも同様に分解できる.
#### 
**DPwalk decomposition**: 純粋な$d$次元単体複体$X$と任意の$0\le i\le d,f,g\in \ispace$に対し,
\[
    \iprod{f,\PDU_i g}&= \E_{\rho\sim X(i-1)}\sbra*{ \E_{\pi^\rho_0}[f_\rho] \cdot \E_{\pi^\rho_0}[g_\rho] }.
\]
上昇ウォークと下降ウォークの随伴性**\cref{eq:adjoint up and walk}**より以下のようにして得られる:
\[
    \iprod{f,\PDU_i g} &= \iprod{f,\Pdown_i \Pup_{i-1} g} \\
    &= \iprod[X(i-1)]{\Pup_{i-1}f, \Pup_{i-1}g } & & \text{$\because$\cref{eq:adjoint up and walk}} \\
    &= \E_{\rho \sim X(i-1)}\sbra*{ \E_{\substack{ \sigma,\sigma'\sim \pi_i\text{ conditioned on }\sigma,\sigma'\supseteq \rho }}\sbra*{f(\sigma)g(\sigma')} } \\
    &= \E_{\rho \sim X(i-1)}\sbra*{ \E_{u,v\sim X_\rho(0)}\sbra*{ f_\rho(u) g_\rho(v)} } \\
    &= \E_{\rho\sim X(i-1)}\sbra*{ \E_{\pi^\rho_0}[f]\cdot \E_{\pi^\rho_0}[g] }
\]

### 第二固有値の比較
**\cref{thm:Kaufman-Oppenheim theorem}**を証明するには$\lambda_2(\PDU_i)$を上から抑える必要がある. そのためにまず$\lambda_2(\PDU_i)$と$\lambda_2(\nonlazyPUD_i)$を比較する.
#### 
**eigenvalue compare**: 純粋な$d$次元単体複体$X$が局所$\gamma$-エクスパンダーであるならば, 任意の$i=0,\dots,d$に対して
\[ \lambda_2(\nonlazyPUD_i) \le \lambda_2(\PDU_i) + \gamma \]
が成り立つ.
$\PDU_i,\nonlazyPUD_i$はどちらも内積$\iprod{\cdot,\cdot}$に関して可逆なので, $\allone$に直交する任意の非ゼロの$f \in \ispace$に対し, **\cref{lem:DPwalk decomposition,lem:nonlazyUP decomposition}**より
\[
    \iprod{f,\nonlazyPUD_i f} - \iprod{f,\PDU_i f} &= \E_{\rho\sim X(i-1)}\sbra*{ \iprod[X_\rho(0)]{f_\rho, P_\rho f_\rho} - \E_{\pi^\rho_0}[f_\rho]^2}  \\
    & \le \E_{\rho \sim X(i-1)}\sbra*{\gamma \inorm[X_\rho(0)]{f_\rho - \E_{\pi^\rho_0}[f_\rho]}^2 } & & \text{$\because$\cref{lem:one side EML}} \\
    &\le \gamma \cdot \E_{\rho\sim X(i-1)}\sbra*{\inorm[X_\rho(0)]{f_\rho}^2} \\
    &= \gamma \inorm{f}^2.
\]
最後の等号は演習問題とする. 移項して整理すると
\[
    \frac{\iprod{f,\nonlazyPUD_i f}}{\inorm{f}^2} &\le \frac{\iprod{f,\PDU_if}}{\inorm{f}^2} + \gamma \\
    & \le \lambda_2(\PDU_i) + \gamma & & \text{$\because$\cref{lem:Rayleigh quotient}}
\]
左辺は$f$に関して最大化すると$\lambda_2(\nonlazyPUD)$となるので主張を得る.

#### 
**pinorm of f**: 上記の証明で用いた等式$\inorm{f}^2  = \E_{\rho \sim X(i-1)}\sbra*{\inorm[X_\rho(0)]{f_\rho}^2}$を示せ.

#### 
**\cref{thm:Kaufman-Oppenheim theorem}の証明**: 全ての$i=0,\dots,d$に対して$\lambda_2(\PDU_i) \le 1-\frac{1}{i+1} + \frac{\gamma i}{2}$を示せばよい. これを$i$に関する帰納法で示す.
$i=0$のとき, $\PDU_0$を考える. $X(0)$上の任意の下降上昇ウォークは必ず面$\emptyset$に遷移し, その後に$X(0)$の頂点に遷移する. このときの遷移確率は$\pi_0$に従って選ばれる. 従って$\PDU_0$は全ての行ベクトルが$\pi_0$であり, 特にランク$1$の行列なので, $\lambda_2(\PDU_0)=0$であり主張は正しい.
一般の$i \ge 1$に対して
\[
    \lambda_2\rbra*{ \PDU_i } &= \lambda_2\rbra*{ \PUD_{i-1} } & & \text{$\because \lambda_2\rbra*{\Pdown_i\Pup_{i-1}}=\lambda_2\rbra*{\Pup_{i-1}\Pdown_i}$} \\
    &= \frac{i}{i+1}\lambda_2\rbra*{ \nonlazyPUD_{i-1} } + \frac{1}{i+1} & & \text{$\because$\cref{def:nonlazy updown}} \\
    &\le \frac{i}{i+1}\lambda_2\rbra*{ \PDU_{i-1}} + \frac{\gamma i + 1}{i+1} & & \text{$\because$\cref{lem:eigenvalue compare}}\\
    &\le \frac{i}{i+1} \rbra*{1 - \frac{1}{i} + \frac{(i-1)\gamma}{2}} + \frac{\gamma i + 1}{i+1} & & \text{帰納法の仮定} \\
    &= 1 - \frac{1}{i+1} + \frac{\gamma i}{2}.
\]
よって主張を得る.

### Alev--Lauの定理
**\cref{thm:Kaufman-Oppenheim theorem}**では, $\gamma < \frac{1}{d^2}$でなければ$\lambda_d$に対する非自明な上界が得られなかった. この問題点は**\citet{AL20}**によって改善され以下の結果が示されている:
#### Alev--Lauの定理
**ALev-Lau theorem**: 純粋な$d$-次元単体複体$X = (V,\F)$が局所$(\gamma_{-1},\dots,\gamma_{d-2})$-エクスパンダーならば,
\[ \lambda_i = 1-\frac{1}{i+1}\prod_{j=-1}^{i-2}(1-\gamma_j)\]
で定義された$\lambda_i$ ($i=0,\dots,d$) に対して$X$は大域$(\lambda_0,\dots,\lambda_{d-1})$-エクスパンダーである.
