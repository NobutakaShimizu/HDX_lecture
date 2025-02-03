---
title: 高次元エクスパンダー概論
nav_order: 4
---

# 高次元エクスパンダー概論

高次元エクスパンダーとはグラフのエクスパンダー性を単体複体に拡張した概念である.
単体複体上では, 大域的なランダムウォークと局所的なランダムウォークの二つのタイプのランダムウォークを自然に考えることができ, これらに基づいてそれぞれ大域的なエクスパンダー性と局所的なエクスパンダー性の概念が定義できる.
端的に述べると高次元エクスパンダーの理論はこれら二つの概念がほぼ等価であることを明らかにしており, これは単体複体における局所大域原理(ここでは局所大域原理(local-global principle)は局所的な情報が大域的な情報を導くという現象の総称として用いるが, もともとは整数論において不定方程式の解の存在性に関するハッセの原理と呼ばれる現象を指す)を体現しているといえる.

本チャプターではまず単体複体とその上でのランダムウォークを定義し,
これに基づいて高次元エクスパンダーの定義と重要な性質を紹介する.

応用なども含めた網羅的なサーベイ論文はまだ私は把握していないが, 本講義資料を作成するにあたり,
この分野の第一線で活躍している海外の研究者らの講義資料を大いに参考にした[^LClec][^Glec][^HLlec].

[^LClec]: Lap Chi Lau. CS 860: Eigenvalues and Polynomials (Lecture Note). 2022. [URL](https://cs.uwaterloo.ca/~lapchi/cs860-2022/notes.html)
[^Glec]: S. O. Gharan. CSE 599: Polynomial Paradigm in Algorithm Design. 2019. [URL](https://homes.cs.washington.edu/~shayan/courses/polynomials/)
[^HLlec]: M. Hopkins and S. Lovett. SE 291 - Expander graphs and High-Dimensional Expanders, 2021. [URL](https://cseweb.ucsd.edu/classes/sp21/cse291-g/)

