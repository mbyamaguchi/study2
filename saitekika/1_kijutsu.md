<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['\$','\$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

# 最適化問題の記述

# 用語の確認

## 問題設定

$
\begin{equation}
\begin{align*}
\min_{\bm{x} \in \mathbb{R}^n} f(\bm{x})  \quad \text{subject to} \quad\bm{x} \in S
\end{align*}
\end{equation}
$

## 実行可能解 feasible solution

最適化問題の**制約**を満たす点。すなわち、**制約** $\bm{x} \in S$ を満たす点を実行可能解という。

## 最適解 optimal solution

問題(1)において、 $\bm{x}^* \in S$ が任意の $\bm{x} \in S$ に対して $f(\bm{x}^*) \leq f(\bm{x})$ を満たすとき、 $\bm{x}^*$ を問題(1)の最適解という。**大域的最適解 global optimal solution**、大域解、最小化元と呼ぶこともある。

## 最適値 optimal value

問題(1)において、目的関数の下限 $\inf \left\{ f(\bm{x}) \mid \bm{x} \in S  \right\}$ の値を最適値という。最適値が存在しても、最適解が存在するとは限らない。

最適解が存在するときには、

$
\inf \left\{ f(\bm{x}) \mid \bm{x} \in S  \right\} = \min \left\{ f(\bm{x}) \mid \bm{x} \in S \right\}
$

が成り立つ。

## 近傍 neighborhood

点 $\bm{x} \in \mathbb{R}^n$ の $\varepsilon$ 近傍 を

$
\begin{equation}
B(\bm{x}, \varepsilon) = \left\{ \bm{y} \in \mathbb{R}^n \mid \| \bm{x} - \bm{y} < \varepsilon \right\}
\end{equation}
$

と定義する。

## 局所最適解 local optimal solution

$\bm{x}^* \in S$ に対して $\varepsilon > 0$ が存在し、

$
\bm{x} \in B(\bm{x}^*, \varepsilon) \cap S \Rightarrow f(\bm{x}^*) \leq f(\bm{x})
$

が成り立つとき、 $\bm{x}^* \in S$ を $f(\bm{x})$ の $S$ 上での局所最適解、または **局所解** という。また、 $f(\bm{x}^*)$ を極小値という。

最適解ならば局所最適解であるが、逆は一般に成立しない。

# 制約について

本書では、

- 制約なし最適化問題
- 等式制約付き最適化問題
- 不等式制約付き最適化問題

を考える。

# 収束速度について

収束速度の評価尺度を以下に示す。

数値解 $\bm{x}_k$ から最適解までの誤差を $\| \bm{x}_k - \bm{x}^* \|$ で測り、収束性 $\lim_{k \rightarrow \inf} \| \bm{x}_k - \bm{x}^* \| = 0$ は保証されているとする。

$
\limsup_{k \rightarrow \inf} \frac{\| \bm{x}_{k+1} - \bm{x}^* \|}{\| \bm{x}_k - \bm{x}^* \|} < 1
$

を満たすなら、数値解 $\{ \bm{x}_k \}_{k=0}^{\infin}$ は $\bm{x}^*$ に **1次収束** するという。

$
\limsup_{k \rightarrow \inf} \frac{\| \bm{x}_{k+1} - \bm{x}^* \|}{\| \bm{x}_k - \bm{x}^* \|} =0
$

となるとき、 **超1次収束** するという。

$
\limsup_{k \rightarrow \inf} \frac{\| \bm{x}_{k+1} - \bm{x}^* \|}{\| \bm{x}_k - \bm{x}^* \|^2} < \infin
$

を満たすとき、 **2次収束** するという。

数値解 $\{ \bm{x}_k \}_{k=0}^{\infin}$ が $\bm{x}^*$ に1次収束するとき、定数 $C > 0$ と $r \in (0,1)$ が存在し、

$
\| \bm{x}_k - \bm{x}^* \| \leq Cr^k
$

が成り立つ。

超1次収束するときは $r_k \searrow 0 \space (k \rightarrow \infin)$ となる数列 $r_k$ が存在して

$
\| \bm{x}_k - \bm{x}^* \| \leq C \prod_{j=1}^k r_j
$

となる。

2次収束するときは、

$
\| \bm{x}_k - \bm{x}^* \| \leq Cr^{2^k}
$

が成り立つ。

すなわち、2次収束は1次収束と比べて非常に収束速度が速いことがわかる。