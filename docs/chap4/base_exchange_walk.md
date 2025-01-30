---
title: 基交換ウォーク
nav_order: 2
parent: マトロイド
---


\section{基交換ウォーク}
\begin{definition}{基交換ウォーク}{basis-exchange walk}
    マトロイド$(V,\F)$の基上の下降上昇ウォークを\emph{基交換ウォーク (basis-exchange walk)}という.
\end{definition}
$X(d-1)$から$X(d)$への上昇ウォークを考えてみよう.
$\pi_{d-1}(\sigma)=\sum_{\tau\in\B} \pi_d(\tau) \cdot \Pdown_d(\tau,\sigma)$は, $\pi_d$が一様分布であり$\Pdown_d(\tau,\sigma)$は$\allone_{\tau\supset \sigma}$に比例するため, $\sigma$を含む基の個数に比例する.
従って
\begin{align*}
    \Pup_{d-1}(\sigma,\tau) = \frac{\pi_d(\tau)\Pdown_d(\tau,\sigma)}{\pi_{d-1}(\sigma)} \propto \allone_{\tau\supset \sigma}
\end{align*}
を得る.
すなわち, 基$B$から開始する基交換ウォークは,
一様ランダムに元$u\sim B$を選び,
$B\setminus u$を含む基の中から一様ランダムな基$B'\in B'$に遷移するランダムウォークであり, その定常分布は一様分布である.
基交換ウォークの混交時間のバウンドは長年の未解決問題であった.
\begin{conjecture}{Mihail--Vazirani予想}{Mihail-Vazirani}
    任意のマトロイド$M=(V,\F)$上の基交換ウォークの混交時間は$|V|$に関する多項式で上から抑えられる.
    すなわち, $M$に依存しないある定数$c>0$が存在して
    \[
        \tmix(1/2) \le |V|^c.
    \]
\end{conjecture}
基全体の個数は$\abs{V}$に関して指数関数的であるが,
ここでは
\emph{多項式ステップ}の基交換ウォークで混ざり合うかを問うている.
グラフ的マトロイドといった特殊ケースでは\cref{conj:Mihail-Vazirani}が正しいことが知られていた
\cite{balanced_matroids}が, 一般のマトロイドで正しいかどうかは未解決であった.

