---
title: 局所エクスパンダー性
nav_order: 3
parent: 高次元エクスパンダー概論
---


\section{局所エクスパンダー性}
単体複体における局所的なランダムウォークを定義し, これに基づいて単体複体の局所エクスパンダー性を定義する.
また, 局所エクスパンダー性を確認するための非常に強力な定理としてOppenheimのトリクルダウン定理を証明する.

\subsection{局所的なランダムウォーク}
各リンク$X_\sigma$の$1$-スケルトン上での局所的な重み付きランダムウォークを考える.
重み付きランダムウォークについては\cref{def:weighted random walk}を参照されたい.
%
\begin{definition}{局所ランダムウォーク}{local random walk}
    純粋な$d$次元単体複体$X = (V,\F)$を考える.
    次元$i \le d-2$の面$\sigma \in \F$に対し,
        リンク$X_\sigma$の$1$-スケルトンを$G_\sigma = (V_\sigma,E_\sigma)$とする.
    このグラフの辺重み$w_\sigma\colon E_\sigma \to [0,1]$を
    \[ w_\sigma(e) = \pi_{i+2}(\sigma\cup e) \]
    で定め, これによって定まる$V_\sigma$上の重み付きランダムウォークを面$\sigma$に関する\emph{局所ランダムウォーク (local random walk)}と呼び%\footnote{このランダムウォークの概念は高次元エクスパンダーの文脈ではほぼ必ず登場するが, 特に標準的な用語が与えられてはいないので、「局所ランダムウォーク」という用語は本講義だけの局所的なものとする.}
    , 遷移確率行列を$P_\sigma\in [0,1]^{V_\sigma\times V_\sigma}$とする.
\end{definition}
%
必ずしも局所ランダムウォークが既約性や非周期性を持つとは限らない(すなわち, グラフ$G_\sigma$が非連結だったり二部グラフになりうる)が,
可逆性は必ず満たすことに注意せよ.

グラフ($1$次元単体複体)だと面$\emptyset$に対する局所ランダムウォークのみ定義できるが, これは上昇下降ウォーク(すなわち遅延単純ランダムウォーク)と同じである.
従って局所ランダムウォークの概念はより高次元の単体複体を考える際に意味を持つ.
簡単な計算から, 遷移確率行列$P_\sigma$の各成分は以下のように表せる.
\begin{lemma}{}{local RW seibun}
    面$\sigma \in X(i)$ (ただし$i\le d-2$) に関する局所ランダムウォークの遷移確率行列$P_\sigma$の各成分は
    \begin{align*}
        P_\sigma(u,v) &= \begin{cases}
            	\frac{\pi_{i+2}(\sigma\cup\{u,v\})}{(i+3)\pi_{i+1}(\sigma\cup\{u\})}& \tif \{u,v\}\in E_\sigma,\\
        0 & \totherwise.
        \end{cases}
    \end{align*}
\end{lemma}
%
\begin{exercise}{}{local RW seibun}
    \cref{lem:local RW seibun}を示せ.
\end{exercise}
%
%\begin{lemma}{}{local random walk stationary distribution}
%    遷移確率行列$P_\sigma$をもつ局所ランダムウォークの定常分布を$\pi_\sigma$とすると, 
%\end{lemma}
%
\subsection{局所エクスパンダー}
純粋な単体複体の局所的なエクスパンダー性を定義する.
任意の面$\sigma$に対し$G_\sigma$上での局所ランダムウォークの第二固有値が小さいとき, その単体複体は局所的エクスパンダー性をもつという.
\begin{definition}{局所エクスパンダー性}{local expander}
    純粋な$d$次元単体複体$X=(V,\F)$を考える.
    任意の$i=-1,0,\dots,d-2$と任意の面$\sigma\in X(i)$に対し
    $\lambda_2(P_\sigma)\le \gamma_i$を満たすとき,
    \emph{局所$(\gamma_{-1},\dots,\gamma_{d-2})$-エクスパンダー (local spectral $(\gamma_{-1},\dots,\gamma_{d-2})$-expander)}であるという.
    特に, $\gamma_{-1}=\dots=\gamma_{d-2} = \gamma$であるとき, 局所$\gamma$-エクスパンダーであるという.
\end{definition}
あくまでも$G_\sigma$の片側エクスパンダー性のみを議論していることに注意.
従って, 局所エクスパンダーだからといって$G_\sigma$上の局所ランダムウォークの混交時間が小さいとは限らない (そもそも二部グラフになりうるので, 一般に収束しない).


\paragraph*{例1. 三角形複体.}
グラフ$G=(V,E)$上の頂点数$3$以下のクリークからなる単体複体を$X$とする (\cref{sec:define simplicial complex}の例6参照).
頂点$u \in V$のリンク$X_u \defeq X_{\{u\}}$を考える.
$u$の隣接頂点の集合を$N(u)$とする.
$G$辺$\{u,v_1\},\{u,v_2\}\in E$に対し, $\{v_1,v_2\}\in E$のときに三角形$\{u,v_1,v_2\}$が単体複体$X$の面となる.
従って, リンク$X_u$は頂点$u$の誘導部分グラフ$G[N(u)\setminus\{u\}]$に等しい .
また, 全ての三角形に対し一様な重みを与えているため, $G_u$上のランダムウォークは単純ランダムウォークと同一である.
\begin{figure}
    \begin{center}
    \includegraphics[width=10cm]{images/localwalk1.png}
    \caption{頂点$u$のリンクの2-スケルトン$G_u$は頂点$u$の隣接頂点からなる誘導部分グラフである.}
    \end{center}
\end{figure}
\paragraph*{例2. 全域木複体.}
連結グラフ$G=(V,E)$上の森からなる辺集合$E$上の単体複体を$X$とする (\cref{sec:define simplicial complex}の例3参照).
極大でない森$\sigma\subseteq E$に対するリンクの$1$-スケルトン$G_F$を考える.
このグラフの頂点集合は$E\setminus \sigma$であり, $e_1,e_2 \in E \setminus \sigma$が$G_\sigma$上で辺をなすのは$\sigma \cup \{e_1,e_2\}$が森でありかつその時に限る.

さて, $G$の部分グラフ$(V,\sigma)$を考えよう ((\cref{fig:tree link}).).
森$\sigma$の非極大性からこの部分グラフは二つ以上の連結成分$C_1,\dots,C_\ell \subseteq V$からなる.
従って, $e_1,e_2\in E\setminus \sigma$が森であることの必要十分条件は$e_1,e_2$が同じ連結成分間を繋がないことである.
\begin{figure}
    \begin{center}
    \includegraphics[width=8cm]{images/forest_link.png}
    \caption{赤, 青, 黄の辺からなる森を$\sigma$とする. 同じ連結成分の間を結ぶ二つの辺は$G_\sigma$上では隣接しない. \label{fig:tree link}}
    \end{center}
\end{figure}
