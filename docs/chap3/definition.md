---
title: 定義
nav_order: 1
parent: 高次元エクスパンダー概論
---


\section{定義} \label{sec:define simplicial complex}
まずは単体複体に関する基礎的な用語を定義していく.
文脈によっては単体複体は多面体などを貼り合わせた幾何的な図形を指すこともあるが,
本講義ではいわゆる抽象的単体複体を単体複体とする.
\begin{figure}
    \begin{center}
    \includegraphics[width=12cm]{images/face.png}
    \caption{各面の図形的な意味合い. \label{fig:face}}
    \end{center}
\end{figure}

\begin{definition}{単体複体}{simplicial complex}
有限集合$V$と$V$の部分集合族$\F\subseteq 2^V$であって部分集合で閉じているもの(すなわち, $\sigma\subseteq \tau \in \F \Rightarrow \sigma\in \F$)の組$X=(V,\F)$を\emph{単体複体 (simplicial complex)}という.
\begin{itemize}
\item 集合族$\F$の元を\emph{面 (face)}と呼び,
面$\sigma \in \F$の\emph{次元 (dimension)}を$\dim \sigma = \abs{\sigma} - 1$とする\footnote{特に, 空集合$\emptyset \in \F$の次元は$-1$である.}.
単体複体$X$の次元を$\dim X = \max\cbra{\dim \sigma \colon \sigma \in \F}$とする.

\item 次元$d$の単体複体$X$は(包含関係に関して)極大な面の次元が全て$d$に等しいとき, \emph{純粋 (pure)}であるという.

\item 整数$-1 \le k \le \dim X$に対し$X(k) = \cbra*{\sigma \in \F\colon \dim \sigma = k }$とする.
特に断りのない限り, $X(0)=V$を仮定する
(そうでなければ$V$として$V=X(0)$とした単体複体を考える).

\item 純粋な$d$-次元単体複体$X$に, $d$次元の面全体$X(d)$上の何らかの分布$\pi \in [0,1]^{X(d)}$が付随している場合, $X$を\emph{重み付き単体複体 (weighted simplicial complex)} (もしくは$\pi$で重みつけられた単体複体)と呼ぶ.
\end{itemize}
以後, 単体複体といった場合, 暗に重み付き単体複体を考え, 最大次の面の重みを$\pi$で表す.
\end{definition}
面の次元の概念は単体複体の幾何的な表現に由来する.
このイメージになぞらえて,
次元$0$の面を\emph{頂点 (vertex)}, 次元$1$の面を\emph{辺 (edge)}と呼ぶことがある.

記法の簡単のため, 面$\sigma$と頂点$u\in V$に対し$\sigma \setminus \{u\}$を簡略化して$\sigma \setminus u$と書くこともある.

\paragraph*{例1.}
グラフ$G=(V,E)$に対し, 空集合, $V$, $E$からなる部分集合族
$\F = \{\emptyset\} \cup \cbra*{\{v\}\colon v \in V} \cup E$考えると,
$(V,\F)$は単体複体である.

\paragraph*{例2.}
有限集合$V$に対し,
\begin{align}
    \F = \binom{V}{\le k} \defeq \cbra*{ \sigma \subseteq V \colon |\sigma|\le k} \label{eq:uniform matroid}
\end{align}
としたとき, $(V,\mathcal{F})$は純粋な$(k+1)$-次元の単体複体である.

\paragraph*{例3.}
閉路を含まないグラフを\emph{森 (forest)}といい, 連結な森を\emph{木 (tree)}という.
連結グラフ$G$の部分グラフであって木であるものを\emph{全域木 (spanning tree)}という (cf. \cref{def:graph}).
グラフ$G=(V,E)$に対し,
森であるような部分グラフの辺集合からなる集合族$\F\subseteq 2^E$は単体複体である.
すなわち,
\begin{align}
    \F = \cbra*{ F \subseteq E \colon \text{部分グラフ$(V,F)$は森}} \label{eq:graphic matroid}
\end{align}
に対して$(E,\F)$は単体複体である.
簡単のため$G$を連結グラフであるとすると, $(E,\F)$の極大面は$G$の全域木に対応し, その次元は$n-2$に等しい.
すなわち$(E,\F)$は純粋な$(n-2)$-次元単体複体である.

なお, グラフ$G$が連結でない場合, 異なる連結成分に属する二頂点$u,v$を縮約し一つの頂点として扱うことによって単体複体$(E,\F)$を変えないまま元のグラフの連結成分を減らすことができるので, 連結性を仮定しても一般性を失わない.

\paragraph*{例4.}
ベクトル$\vec{a_1},\dots,\vec{a_n} \in \Real^m$を考える.
集合$V=\{1,\dots,n\}$の部分集合族であって, 線形独立な行ベクトル集合のインデックスとなるものの全体を$\F$とする.
すなわち
\begin{align}
    \F = \cbra*{ I \subseteq V\colon (\vec{a_i})_{i\in I}\text{は線形独立}} \label{eq:linear matroid}
\end{align}
とすると, $(V,\F)$は純粋な単体複体である.

\paragraph*{例5.}
部集合$L,R$を持つ二部グラフ$G=(V,E)$を考える.
辺部分集合$M\subseteq E$は, 部分グラフ$(V,M)$の全ての頂点の次数が高々$1$であるとき\emph{マッチング (matching)}という.
マッチング$M$の部分集合$M'\subseteq M$もまたマッチングであるため,
グラフ$G$のマッチング全体からなる辺部分集合族$\F\subseteq 2^E$に対し, $(E,\F)$は単体複体である.
一般に極大マッチングのサイズは異なる場合があるのでこの単体複体は純粋ではない (\cref{fig:matching}).
\begin{figure}[htbp]
    \begin{center}
        \includegraphics[width=5cm]{images/matching.pdf}
    \end{center}
    \caption{マッチング$M_1=\{v_1,v_2\},\{v_3,v_4\}\}$と$M_2=\{\{v_2,v_3\}\}$はどちらも極大である. \label{fig:matching}}
\end{figure}

\paragraph*{例6.}
グラフ$G=(V,E)$の頂点部分集合$U\subseteq V$は, $U$に属する任意の二頂点間に辺がある(すなわち$\binom{U}{2}\subseteq E$)とき, \emph{クリーク (clique)}\footnote{cliqueとは派閥を意味する英単語である.}という.
特に, 単一頂点からなる集合$\{u\}$や$\emptyset$もクリークである.
クリークの部分集合もまたクリークなので,
グラフ$G$の全てのクリークからなる頂点集合族を$\F$とすると, $(V,\F)$は単体複体である.
これをグラフの\emph{クリーク複体 (clique complex)}と呼ぶ.

\begin{definition}{リンクとスケルトン}{link and skelton}
    単体複体$X=(V,\F)$を考える.
    面$\sigma \in \F$の\emph{リンク (link)}とは単体複体$(V\setminus \sigma, \F_{\sigma})$であって集合族$\F_\sigma$が
    \[
        \F_\sigma = \cbra*{ \tau \setminus \sigma \colon \sigma \subseteq \tau \in \F }
    \]
    で与えられるものである.
    特に, 頂点$v\in X(0)$のリンクは$X_{\{v\}}$の代わりに$X_v$で表す.

    次元$k$以下の面の集合
    \[
        \F_k = \cbra*{ \sigma \in \F \colon \dim \sigma \le k}
    \]
    に対し$(V,\F_k)$を\emph{$k$-スケルトン ($k$-skelton)}という.
\end{definition}
\begin{figure}
    \begin{center}
    \includegraphics[width=12cm]{images/forest_link_shirnk.png}
    \caption{
        赤, 青, 黄の辺からなる森を$\sigma$としたとき, $\sigma$を縮約して得られるグラフ上の森がリンク$X_\sigma$の面に対応する.
        \label{fig:forest_link_shrink}.}
    \end{center}
\end{figure}
面$\sigma$のリンクとは, $\sigma$を「縮約」して得られる単体複体であり, 面$\sigma$の周りの局所的な構造を表している.
例えば連結グラフ$G=(V,E)$の森の全体からなる単体複体$X=(E,\F)$を考えよう.
$\sigma\in \F$を一つ固定したとき, リンク$X_\sigma$はどのような単体複体になっているだろうか?
$X_\sigma$の全ての面は辺集合$\sigma$を含むので, $\sigma$に含まれる全ての頂点を縮約して得られるより小さなグラフを考え, そこから$\sigma$の辺を除去して得られるグラフ$G'$の森全体からなる単体複体とみなせる (\cref{fig:forest_link_shrink}).
マトロイドの文脈では縮約と呼ばれる操作と同じである.

本講義では基本的に$1$-スケルトンのみ扱う.
単体複体の$1$-スケルトンは, $1$次元の面を辺とみなすことでグラフと同一視できる.
以後, $1$-スケルトンといった場合はこの同一視によってグラフとして扱う.

純粋な$d$次元単体複体$X$の面$\sigma\in X(i)$のリンク$X_\sigma$は純粋な$(d-i-1)$次元単体複体である.
特に$X_\emptyset = X$である.

%\end{definition}
