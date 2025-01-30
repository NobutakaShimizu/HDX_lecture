---
title: 局所エクスパンダー性
nav_order: 3
parent: マトロイド
---


\section{マトロイドの局所エクスパンダー性}
本節では以下の定理を証明する.
\begin{lemma}{}{local expander matroid}
    任意のマトロイド$(V,\F)$は局所$0$-エクスパンダーである.
\end{lemma}


\subsection{Oppenheimのトリクルダウン定理}
ある単体複体$X$に対して局所エクスパンダー性(\cref{def:local expander})を示すには全ての面に対して$\lambda_2(P_\sigma)$を上から抑える必要がある.
一般にそもそも辺重み$w_\sigma$ (\cref{def:local random walk}) を求めることすら非自明であり, ましてや固有値を抑えるなど非常に大変な作業となる.
Oppenheimのトリクルダウン定理\cite{Oppenheim_tricling_down}は局所エクスパンダー性を確認するのに非常に有用な定理である.
\begin{theorem}{Oppenheimのトリクルダウン定理}{Oppenheim trickle-down theorem}
    純粋な重み付き$d$-次元単体複体$X = (V,\F)$が以下の二つを満たすとする:
    \begin{itemize}
    \item 全ての$i\le d-2$と全ての$\sigma\in X(i)$に対してグラフ$G_\sigma$は連結.
    \item 全ての$(d-2)$-次元の面$\tau \in X(d-2)$に対して$\lambda_2(P_\tau) \le \gamma$.
    \end{itemize}
    このとき, $\gamma_i \defeq \frac{\gamma}{1-(d-2-i)\gamma}$ ($i=-1,\dots,d-2$)に対して$X$は局所$(\gamma_{-1},\dots,\gamma_{d-2})$-エクスパンダーである.
\end{theorem}
端的に言えば, 次数$d-2$の面$\sigma \in X(d-2)$に対して$\lambda(P_\sigma)$を抑えれば全ての次元の面に対しても第二固有値が上から抑えられるという結果である.
最上次元の面のエクスパンダー性が下次元の面に波及していくという意味ではまさに「トリクルダウン(浸透)」といえよう.

一つ目のグラフ$G_\sigma$の連結性の条件は不可欠である.
例えば二つの完全グラフからなる非連結グラフ上の三角形複体を考えると,
空集合以外の全てのリンクは完全グラフ上のランダムウォークとなるため$\gamma=0$に対して二つ目の条件を満たすが, $\sigma=\emptyset$に対して$G_\sigma$は非連結であるため$\gamma_{-1}=0$にはならない.


\cref{thm:Oppenheim trickle-down theorem}は, まず$d=2$の特殊ケースで証明し, 一般の$d$についてはこの特殊ケースに帰着する.
%
\begin{lemma}{\texorpdfstring{$d=2$}{2次元}におけるトリクルダウン定理}{trickle-down for 2dim}
    純粋な重み付き$2$次元単体複体$X=(V,\F)$の各頂点$v\in X(0)$における局所ランダムウォーク$P_v$が$\lambda_2(P_v) \le \gamma$を満たし, かつその$1$-スケルトン$G_v$が連結ならば, 面$\emptyset$における局所ランダムウォーク$P_\emptyset$は
    \[
        \lambda_2(P_\emptyset) \le \frac{\gamma}{1-\gamma}
    \]
    を満たす.
\end{lemma}
この補題は本質的に$\gamma<1/2$のときに意味をなす.
\subsection{ランダムウォークの分解}
\cref{lem:trickle-down for 2dim}の証明は,
\cref{thm:Kaufman-Oppenheim theorem}と同様にランダムウォークを分解することから始まる.
記法の簡単のため, 頂点$u$のリンクを$X_{\{u\}}$の代わりに$X_u$, 遷移確率行列を$P_{\{u\}}$の代わりに$P_u$と表す.
\begin{definition}{}{localize}
    重み付き単体複体$(V,\F)$, 頂点$u\in V$, 関数$f \in \ispace[X(0)]$に対し,
    関数$f^u \in \ispace[X_u(0)]$を$f$の$X_u(0)$への制限, すなわち
    \[
        f^u (v) = f(v)
    \]
    とする.
\end{definition}
簡単な計算から以下の二次形式の分解補題が成り立つことがわかる.
\begin{lemma}{}{decomposition}
    任意の$f,g\in \ispace[X(0)]$に対して
    \[
        \iprod[X(0)]{f,g} = \E_{u\sim X(0)}\sbra*{ \iprod[X_u(0)]{f^u,g^u} }.
    \]
    また, 面$\emptyset$上の局所ランダムウォークの遷移確率行列を$P_\emptyset \in [0,1]^{X(0)\times X(0)}$とすると,
    \[
        \iprod[X(0)]{P_\emptyset f,g} = \E_{w\sim X(0)}\sbra*{ \iprod[X_u(0)]{P_uf^u,g^u} }.
    \]
\end{lemma}
\begin{proof}
    最初の等式を示す:
    \begin{align*}
        (\text{左辺}) &= \E_{u\sim X(0)} \sbra*{ f(u) g(u) } \\
        &= \E_{e \sim X(1)}\sbra*{ \E_{v \sim e} \sbra*{f(v)g(v)}} & & \text{$v\sim e$の周辺分布は$\pi_0$}\\
        &= \E_{u\sim X(0)} \sbra*{ \E_{\substack{e=\{u,v\} \sim X(1) \\ \text{conditioned on }e\ni u} }\sbra*{ f(v)g(v) }} & & \text{$e\sim X(1)$の$v$でない方の端点$u$を先に選ぶ}\\
        &= \E_{u\sim X(0)}\sbra*{ \E_{v \sim X_u(0)} \sbra*{f^u(v) g^u(v)} } & & \text{$\because$\cref{rem:link of u}}\\
        &= (\text{右辺}).
    \end{align*}
    二つ目の等式を示す.
    \begin{align*}
        (\text{左辺}) &= 
        \E_{\substack{u\sim X(0)\\ v\sim P_\emptyset(u,\cdot)}} \sbra*{ f(u)g(v)}\\
        &= \E_{t \sim X(2)}\sbra*{ \E_{\substack{w \sim t \\ u \sim t\setminus \{w\}, \\ \{v\}=t\setminus\{u,w\}}} \sbra*{f(u)g(v)} } \\
        &= \E_{w\sim X(0)}\sbra*{ \E_{\substack{t \sim X(2) \\ \text{conditioned on }t \ni w \\ u \sim t \setminus w \\ \{v\}=t\setminus\{u,w\}}} \sbra*{f(u)g(v)} } & & \text{前式の$w$の周辺分布は$X(0)$}\\
        &= \E_{w\sim X(0)}\sbra*{ \E_{\substack{u\sim X_w(0) \\ v\sim P_w(u,\cdot)}}\sbra*{f(u)g(v)} } \\
        &= (\text{右辺}).
    \end{align*}
\end{proof}
%
\begin{proof}[\textbf{\cref{lem:trickle-down for 2dim}の証明.}]
    記号の簡単のため$P=P_\emptyset$とする.
    局所ランダムウォーク$P$の第二固有値に対応する固有ベクトルを$f$とする.
    正規化して$\inorm[X(0)]{f}=1$とする.
    $P_\emptyset$の可逆性および\cref{lem:Rayleigh quotient}から,
    $\iprod[X(0)]{f,\allone}=0$である.
    補題を証明するには, $ \lambda_2(P)=\iprod[X(0)]{P f,f}$を上から抑えればよい.

    各頂点$u \in X(0)$に対し\cref{def:localize}で定義された$f^u \in \ispace[X_u(0)]$を考える.
    このベクトルを直交分解し,
    \begin{align}
        f^u = \alpha_u \allone^u + \overline{f^u} \label{eq:eigen decomposition fu}
    \end{align}
    と表す.
    ここで, $\allone^u \in \ispace[X_u(0)]$は全成分が$1$のベクトルで, $\alpha_u=\iprod[X_u(0)]{f,\allone^u}$であり, $\overline{f^u}$は$\allone^u$に直交するベクトルである.

    直交分解(\ref{eq:eigen decomposition fu})を用いると
    \begin{align*}
        \iprod[X_u(0)]{P_u f^u,f^u} &= \iprod[X_u(0)]{P_u\rbra*{\alpha_u\allone^u + \overline{f^u}}, \alpha_u\allone^u+\overline{f^u}} \\
        &= \iprod[X_u(0)]{\alpha_u \allone^u + P_u\overline{f^u}, \alpha_u\allone^u+\overline{f^u}} \\
        &= \alpha_u^2 + \iprod[X_u(0)]{P_u\overline{f^u},\overline{f^u}}  & & \text{直交性よりクロスタームは消える}\\
        &\le \alpha_u^2 + \gamma\inorm[X_u(0)]{\overline{f^u}}^2 & & \text{$\because$$\lambda_2(P_u)\le \gamma$および\cref{lem:Rayleigh quotient}}
    \end{align*}
    を得る.
    \cref{lem:decomposition}より,
    \begin{align*}
        \lambda_2(P) &= \iprod[X(0)]{Pf,f} \\
        &= \E_{u\sim X(0)}\sbra*{ \iprod[X_u(0)]{P_u f^u,f^u} } & & \text{$\because$\cref{lem:decomposition}の二つ目の等式} \\
        &\le \E_{u\sim X(0)}\sbra*{\alpha_u^2} + \gamma\cdot \E_{u\sim X(0)}\sbra*{\inorm[X_u(0)]{\overline{f^u}}^2} & & \text{直前の不等式を代入}\\
        &= \gamma\cdot \E_{u\sim X(0)}\sbra*{\alpha_u^2 + \inorm[X_u(0)]{\overline{f^u}}^2} + (1-\gamma)\cdot \E_{u\sim X(0)}\sbra*{\alpha_u^2} \\
        &= \gamma\cdot \E_{u\sim X(0)}\sbra*{\inorm[X_u(0)]{f^u}^2} + (1-\gamma)\cdot \E_{u\sim X(0)}\sbra*{\alpha_u^2} & & \text{$\because$$f^u$に対する三平方の定理}\\
        &= \gamma \cdot \inorm[X(0)]{f}^2 + (1-\gamma)\cdot \E_{u\sim X(0)}\sbra*{\alpha_u^2} & & \text{$\because$\cref{lem:decomposition}を$\iprod[X(0)]{f,f}$に適用} \\
        &= \gamma + (1-\gamma)\cdot \E_{u\sim X(0)}\sbra*{\alpha_u^2} & & \text{$f$のノルムは$1$}
    \end{align*}
    を得る.
    従って, $\E_{u\sim X(0)}\sbra*{\alpha_u^2}$を上から抑えたい.

    内積$\iprod[X_u(0)]{\cdot,\cdot}$の定義から
    \begin{align*}
        \alpha_u &= \iprod[X_u(0)]{f^u,\allone^u} \\
        &= \E_{v \sim X_u(0)}\sbra*{f^u(v)} \\
        &= \E_{v \sim X_u(0)}\sbra*{ f(v) } & & \text{\cref{def:localize}参照}\\
        &= (Pf)(u) & & \text{$P=P_\emptyset$は$1$-スケルトン上のランダムウォーク}
    \end{align*}
    であり, $f$は$P$の固有ベクトルなので
    \begin{align*}
        \E_{u\sim X(0)}\sbra*{\alpha_u^2} &= \inorm[X(0)]{Pf}^2 = \lambda_2(P)^2.
    \end{align*}
    これを代入すると二次不等式
    \begin{align*}
        \lambda_2(P) \le \gamma + (1-\gamma)\lambda_2(P)^2
    \end{align*}
    を得る. これを$\lambda_2(P)$について解くと
    \[
     \lambda_2(P)\ge 1 \text{ または }\lambda_2(P) \le \frac{\gamma}{1-\gamma}
    \]
    となるが, $1$-スケルトン$G_v$の連結性の仮定より$\lambda_2(P)<1$なので, $\lambda_2(P) \le \frac{\gamma}{1-\gamma}$を得る.    
\end{proof}
%
\subsection{トリクルダウン定理の証明}
\cref{lem:trickle-down for 2dim}を用いて一般の次元$d$に対する\cref{thm:Oppenheim trickle-down theorem}を証明する.
%
\begin{proof}[\textbf{\cref{thm:Oppenheim trickle-down theorem}の証明.}]
    $X=(V,\F)$を純粋な重み付き$d$次元単体複体とする ($d\ge 3$).
    面$\sigma \in X(d-3)$のリンク$X_\sigma$の次元は$2$であり,
    $X_\sigma$の頂点$v\in X_\sigma(0)$に対して
    $\sigma \cup \{v\} \in X(d-2)$より,
    $X_\sigma$上の$v$における局所ランダムウォークの遷移確率行列は$P_{\sigma\cup \{v\}}$に等しく, 仮定より$\lambda_2\rbra*{P_{\sigma\cup\{v\}}}\le \gamma$である.
    さらに, $X$の各リンクの$1$-スケルトンは連結なので, \cref{lem:trickle-down for 2dim}より
    \[
        \lambda_2(P_\sigma) \le \frac{\gamma}{1-\gamma}
    \]
    を得る.
    同じ議論を, $X$をその$(d-1)$-スケルトンに置き換えて適用すると,
    任意の$\sigma' \in X(d-4)$に対し
    \[
        \lambda_2(P_{\sigma'}) \le \frac{\frac{\gamma}{1-\gamma}}{1- \frac{\gamma}{1-\gamma}} = \frac{\gamma}{1-2\gamma}
    \]
    を得る.
    これを繰り返すと, ($j$に関する帰納法により)
    面$\rho \in X(d-2-j)$に対し
    \[
        \lambda_2(P_\rho) \le \frac{\gamma}{1-j\gamma}
    \]
    を得る.
\end{proof}
%

