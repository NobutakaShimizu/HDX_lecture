---
title: 大域エクスパンダー性
nav_order: 2
parent: 高次元エクスパンダー概論
---


\section{大域エクスパンダー性}
グラフ上のランダムウォークは頂点集合上で遷移するものを考えていたが,
単体複体上のランダムウォークは異なる次元の面の間で遷移するものを考える.
具体的には, \cref{sec:graph up and down walk}で考えたようにある次元$i$の面から次元$i+1$の面に遷移する上昇ウォークと逆に次元$i+1$の面から次元$i$の面に遷移する下降ウォークである.
上昇ウォークと下降ウォークが互いに随伴の関係になるようにするため, 各$X(i)$上での定常分布を定義し, $X(i)$と$X(i+1)$の間で詳細釣り合い条件が満たされるように定義される.

\subsection{下降ウォークと定常分布}
まず, \cref{sec:graph up and down walk}で考えた下降ウォークを単体複体に拡張し, $X(d)$上では一様分布を定常分布とすることによって帰納的に各$X(i)$上での定常分布を定める.
\begin{definition}{下降ウォークと面上の定常分布}{down walk and stationary distribution}
    $\pi$で重み付けられた純粋な$d$次単体複体$X=(V,\F)$を考える.　
    各$i=0,\dots,d$に対し
        確率行列$\Pdown_i \in [0,1]^{X(i) \times X(i-1)}$を
        \[
            \Pdown_i(\tau,\sigma) = \begin{cases}
                \frac{1}{i+1}	& \tif \sigma \subseteq \tau,\\
                0 & \totherwise
            \end{cases}
        \]
        とし, $X(i)$上の分布$\pi_i \in [0,1]^{X(i)}$を
        \begin{itemize}
        \item $i=d$のとき, $\pi_d = \pi$とする.
        \item $i<d$に対しては帰納的に$\pi_i = \pi_{i+1}\Pdown_{i+1}$とする.
        \end{itemize}
    各$i$に対し分布$\pi_i$を$X(i)$上の($i$次の)\emph{定常分布}と呼ぶ.

    以後, 面$X(i)$には暗に定常分布$\pi_i$が付随しているとする.
    すなわち, $u \sim X(i)$と書いた場合は$u\sim \pi_i$を意味する.
\end{definition}
面$\tau \in X(i+1)$に対して$\Pdown_{i+1}(\tau,\cdot)$で定まる$X(i)$上の分布は, 面$\tau$に含まれる頂点$u$を一様ランダムに選んだときの$\sigma = \tau \setminus\{u\}$の分布と等しい (\cref{fig:stationary_distribution}).
この分布は, まず定常分布に従って$X(d)$から面を選び, その中から一様ランダムに選ばれた$i+1$個の頂点からなる$X(i)$の面のなす分布でもある.
例えば$\pi$が一様分布のとき, $\pi_i(\sigma)$は$\sigma$を含む極大な面の個数に比例する.
これは遅延単純ランダムウォークの定常分布$\pi(u)$が次数$\deg(u)$に比例することの一般化である.

\begin{figure}[htbp]
    \begin{center}
    \includegraphics[width=\linewidth]{images/stationary_distribution.png}
    \caption{最大次の面を重み$\pi$に従ってランダムに選び, そこから一様ランダムな頂点を一つずつ消していくときの各次元での周辺分布が$\pi_i$となる. この仮定が下降ウォークである. \label{fig:stationary_distribution}}
    \end{center}
\end{figure}


ある面$\tau\in X(i+1)$から分布$\Pdown_{i+1}(\tau,\cdot)$に従ってランダムに選ばれた面$\sigma$に遷移する過程を\emph{下降ウォーク (down walk)}と呼ぶ.

各リンクに対しても同様に定常分布を定義する.
\begin{definition}{リンク上の定常分布}{link stationary distribution}
    純粋な$d$次元単体複体$X$のリンク$X_\sigma$ ($\sigma \in X(i)$)に対して最大次の定常分布$\pi^{\sigma}_{d-i-1}$を
    \begin{align*}
        \pi^\sigma_{d-i-1}(\alpha) &= \Pr_{\tau\sim\pi_{d}}\sbra*{\tau=\alpha\cup \sigma \condition \tau\supseteq \sigma}
    \end{align*}
    で定め, それ以下の次元の定常分布$\pi^\sigma_j$は\cref{def:down walk and stationary distribution}によって定める.

    以後, $u\sim X_\sigma(j)$と書いたとき, $u \sim \pi^\sigma_j$を意味する.
\end{definition}
リンク上の$j$次の定常分布$\pi^\sigma_j$は
\begin{align}
    \pi^\sigma_j(\alpha) = \Pr_{\tau \sim X(i+j+1)}\sbra*{\tau = \alpha \cup \sigma \condition \tau \supseteq \sigma} \propto \pi_{i+j+1}(\alpha\cup\sigma) \label{eq:pi alpha j}
\end{align}
を満たす.
特に$\sigma=\emptyset$とすれば, $i=\dim(\sigma)=-1$より$\pi^\emptyset_j = \pi_j$が成り立つ.

\begin{remark}{}{link of u}
    定義を咀嚼するために, ここでは頂点$u\in V$のリンク$X_u$に対して$0$次の定常分布を考えてみよう.
    $X_u(0)=\{v \in V \colon \{u,v\}\in X(1)\}$であり, これは$1$-スケルトンにおける$u$の隣接頂点の集合に等しい.
    ランダムな辺$e \sim X(1)$に対して端点のどちらか$v \sim e$を一様ランダムに選んだときの$v$の周辺分布が$\pi_0$となる.
    一方で, 固定した頂点$u$に対し, $u$を含むよう条件つけて$e \sim X(1)$をサンプリングしたとき, $u$でない方の端点$v$の分布が$\pi^u_0$となる.
    
    より高次元の面に対しても同様で, \cref{eq:pi alpha j}から分かるように, ある特定の面$\sigma$を含むよう条件つけられた状態で定常分布に従ってサンプリングしたときの$j$次の面の分布が$\pi^\sigma_j$である.
\end{remark}

\subsection{上昇ウォーク}
\cref{def:down walk and stationary distribution}では次元$i$の面から次元$i-1$に遷移する下降ウォークを与えた.
同様に, 次元$i$の面から次元$i+1$の面に遷移する上昇ウォークを, $X(i)$と$X(i+1)$の間の詳細釣り合い条件が成り立つように定義する.
%
\begin{definition}{上昇ウォーク}{up walk}
    純粋な$d$次単体複体$X=(V,\F)$を考える.
    各$i=-1,\dots,d-1$に対し
        確率行列$\Pup_i \in [0,1]^{X(i) \times X(i+1)}$を
    \begin{align*}
        \Pup_i(\sigma,\tau) &= \frac{\pi_{i+1}(\tau)}{\pi_i(\sigma)}\Pdown_{i+1}(\tau,\sigma) \\
        &= \begin{cases}
            \frac{\pi_{i+1}(\tau)}{(i+2)\pi_i(\sigma)}	& \tif \sigma\subseteq \tau,\\
            0 & \totherwise
        \end{cases}
    \end{align*}
    で定める\footnote{全ての$\sigma\in X(i)$に対し$\pi_i(\sigma)>0$である
    (そうでなければ, $\pi$の全成分が正であることに反する).
    }.
\end{definition}
%
簡単な計算により行列$\Pup_i$は確かに確率行列であることが確認できる.

二つの面集合$X(i)$と$X(i+1)$を部集合とする二部グラフを考えればわかりやすい.
それぞれの部集合には$\pi_i,\pi_{i+1}$が定常分布として付随しており,
上昇ウォーク$\Pup_i$と下降ウォーク$\Pdown_{i+1}$は詳細釣り合い条件
\[
    \forall \sigma\in X(i),\tau\in X(i+1),\,\pi_i(\sigma)\Pup_i(\sigma,\tau) = \pi_{i+1}(\tau)\Pdown_{i+1}(\tau,\sigma)
\]
を満たしている.

なお, 下降ウォーク$\Pdown_{i}$と上昇ウォーク$\Pup_i$の添字$i$は遷移の開始地点の面の次元としている.
%

\begin{figure}
    \begin{center}
    \includegraphics[width=10cm]{images/walks.png}
    \caption{上昇下降ウォーク$\PDU_i$と下降上昇ウォーク$\PUD_i$ \label{fig:walks}}
    \end{center}
\end{figure}
最後に, 上昇ウォークと下降ウォークを組み合わせることによって面$X(i)$上の二種類のランダムウォークを定義する (\cref{fig:walks}).
\begin{definition}{上昇下降と下降上昇ウォーク}{UD and DU walk}
    \cref{def:down walk and stationary distribution}, \ref{def:up walk}と同じ設定を考える.
    \begin{align*}
        &\PUD_i \defeq  \Pup_i \Pdown_{i+1},\\
        &\PDU_i \defeq \Pdown_{i}\Pup_{i-1}
    \end{align*}
    を遷移確率行列として持つ$X(i)$上のランダムウォークをそれぞれ\emph{上昇下降ウォーク (up-down walk), 下降上昇ウォーク (down-up walk)}と呼ぶ.
    ここで, $X(-1)$上での下降上昇ウォークと$X(d)$上での上昇下降ウォークは定義されない.
\end{definition}
上昇下降ウォークはグラフ上の遅延単純ランダムウォークの自然な一般化になっている (\cref{sec:graph up and down walk}).

\begin{remark}{「上昇」「下降」の名称}{up and down}
    非常にややこしいのだが,
    上昇ウォークと下降ウォークは遷移確率行列を左右どちらから作用させるかによって「上昇」「下降」の意味合いが反転してしまう.
    確率行列としての上昇ウォークは$\Pup_i \in [0,1]^{X(i)\times X(i+1)}$で表せる.
    左から作用させる作用素とみなすと
    $\Pup_i\colon \Real^{X(i+1)} \to \Real^{X(i)}$
    であるので, 上昇ウォークは次元を一つ落とす作用素に見えてしまうのである.
    下降ウォークについても同様である.
    特に上昇下降ウォーク$\PUD_i=\Pup_i\Pdown_{i+1}$を左から作用させると「次元を下げてから上げる」ものになるので, 下降上昇ウォークと混同しやすい.
    
    本講義はランダムウォークを主眼におき, 右から作用させるときの$\Pup_i,\Pdown_i$に興味があるので
    \cref{def:down walk and stationary distribution}, \ref{def:up walk}の呼称を採用している.
    ランダムウォークの遷移確率行列として扱う場合は右から作用させ, 
    内積空間を考え随伴性などを考える場合(\cref{sec:inaiseki})は左から作用させる (このときの行列$P$をマルコフ作用素と呼ぶことがある).

    なお, 可逆なランダムウォーク(\cref{def:reversible})は自己随伴性より, 内積$\piprod{\cdot,\cdot}$の意味では左右どちらから作用させても本質的に同じであるのでこのような煩雑な話は考えなくて良い.
\end{remark}

上昇下降ウォークの性質を述べていく.
\begin{lemma}{定常分布}{UD and DU stationary distribution}
    面$X(i)$上の上昇下降ウォークと下降上昇ウォークはどちらも$\pi_i$を定常分布としてもつ.
\end{lemma}
\begin{proof}
    計算によって簡単に確認できる.
    実際,
    \begin{align*}
        &\pi_i \PUD_i = \pi_i \Pup_i \Pdown_{i+1} = \pi_{i+1} \Pdown_{i+1} = \pi_i, \\
        &\pi_i \PDU_i = \pi_i \Pdown_i \Pup_{i-1} = \pi_{i-1}\Pup_{i-1} = \pi_i
    \end{align*}
    より主張を得る.
\end{proof}
\begin{lemma}{}{PUD seibun}
    上昇下降ウォーク$\PUD_i \in [0,1]^{X(i)\times X(i)}$の各成分は
        \[
            \PUD_i(\sigma,\sigma') = \begin{cases}
                \frac{\pi_{i+1}(\sigma\cup\sigma')}{(i+2)^2\pi_i(\sigma)}
                & \tif \sigma\cup\sigma'\in X(i+1),\\
                \frac{1}{i+2} & \tif \sigma=\sigma', \\
                0 & \totherwise.
            \end{cases}
        \]
\end{lemma}
\begin{exercise}{}{PUD calc}
    \cref{lem:PUD seibun}を示せ.
\end{exercise}


\subsection{各次元の内積空間} \label{sec:inaiseki}
各次元$i$に対して$X(i)$とそれに付随する定常分布を定義できたので, \cref{def:naiseki}の特殊ケースの内積空間を考えることができる.
\begin{definition}{}{naisexi simplicial complex}
    重み付き単体複体$X$の各次元の定常分布を$\pi_i \in [0,1]^{X(i)}$としたとき, $\pi_i$で重みつけられた内積を$\iprod{\cdot,\cdot}$で表す.
    すなわち, 
    \[
        \iprod{f,g} = \sum_{\sigma \in X(i)} \pi_i(\sigma) f(\sigma)g(\sigma)
    \]
    とする.
    また, $\Real^{X(i)}$に内積$\iprod{\cdot,\cdot}$を付随して定まる空間を$\ispace$とし,
    この内積が誘導するノルムを$\inorm{\cdot}$と表す.
\end{definition}
%
上昇ウォーク
$\Pup_i\colon \ispace[i+1] \to \ispace$
と下降ウォーク
$\Pdown_{i+1} \colon \ispace \to \ispace[i+1]$
は互いに随伴の関係にある.
すなわち, 任意の$f\in \ispace[i+1]$と$g\in \ispace$に対して
\begin{align}
    \iprod[X(i+1)]{\Pdown_{i+1} f,g} =
    \iprod{f,\Pup_{i}g}
    \label{eq:adjoint up and walk}
\end{align}
が成り立つ.
%
\begin{exercise}{}{adjoint check}
\cref{eq:adjoint up and walk}を確認せよ.
\end{exercise}

\begin{lemma}{半正定値性}{psd}
    各$i$に対して上昇下降ウォーク$\PDU_i$と下降上昇ウォーク$\PUD_i$は半正定値である.
\end{lemma}
\begin{proof}
    $\PDU_i$と$\PUD_{i-1}$は同じスペクトルを持つので$\PDU_i$についてのみ示せばよい.
    任意の$f\in\ispace$に対し,
    \begin{align*}
        \iprod{f,\PDU_i f} = \iprod{f,\Pdown_i \Pup_{i-1} f} = \iprod[X(i-1)]{\Pup_{i-1}f,\Pup_{i-1}f}\ge 0.
    \end{align*}
\end{proof};


また, リンク$X_\sigma$に対しても\cref{def:link stationary distribution}で定義した定常分布を用いて内積空間$\ispace[X_\sigma(i)]$を定義できる.

単体複体の大域的なエクスパンダー性を下降上昇ウォークのエクスパンダー性で定める.
\begin{definition}{大域エクスパンダー性}{global expander}
    純粋な$d$次元単体複体$X=(V,\F)$は,
    任意の$0\le i \le d$に対して$X(i)$上の下降上昇ウォーク$\PDU_i$が$\lambda_2(\PDU_i)\le \lambda_i$を満たすとき,
    \emph{大域$(\lambda_0,\dots,\lambda_{d})$-エクスパンダー (global $(\lambda_0,\dots,\lambda_{d})$-expander)}であるという.
%    特に, $\lambda_0=\dots=\lambda_{d-1}=\lambda$のとき, 大域$\lambda$-エクスパンダーという.
\end{definition}
エクスパンダーグラフ(\cref{def:expander})と比較すると, 片側(第二固有値)だけの上界だけでエクスパンダー性を定義しているが, \cref{lem:psd}より下からのバウンドがあるので上界だけの保証で十分だらかである.

本講義の目標は単体複体の大域エクスパンダー性を証明することである.
特にマトロイドと呼ばれる単体複体の大域エクスパンダー性はMihail--Vazirani予想\cite{balanced_matroids}と呼ばれる30年来の未解決問題であった\footnote{\cite{balanced_matroids}にはこの予想はMihailとVaziraniが立てたものらしいのだが, この予想を陽に述べた最初の文献は私が調べた限りでは\citet{balanced_matroids}であった.}
が, 2019年に\citet{ALOV24}に解決された.
詳細は\cref{chap:matroid}にて解説する.
