

# Moment Generating Functions 

##  Moments
Other Summaries of data 

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-1"><strong>(\#thm:unnamed-chunk-1) </strong></span>Let $X$ be an r.v. with expectation $E(X) = \mu$, and let $m$ be the median of $X$  

- The value of $c$ that minimizes the mean squared error $E(X - c)^2$ is $c = \mu$  

- The value of $c$ that minimizes the mean absolute error $E |X - c|$ is $c = m$ </div>\EndKnitrBlock{theorem}


\BeginKnitrBlock{proof}<div class="proof">Proof</div>\EndKnitrBlock{proof}


In the case of mean squared error, we have $E(X - c)^2 = \text{Var}(X) + (\mu - c)^2$ according to lemma \@ref(lem:mean-square-expectation). Therefore, the quantity is minimized when $c = \mu$.  

As for the mean absolute error, we need to show that $E|X - m| \le E |X - a|$ for any $a$, which is equivalent to $E(|X - a| - |X - m|) \ge 0$. Assume $m < a$  without loss of generality, if $X \le m$ then 

$$
|X - a| -|X - m| = a-m
$$


and if $X > m$ 

$$
|X - a| - |X - m| \ge X - a - (X- m) = m -a
$$

Let 

$$
Y  = |X - a| - |X - m|
$$

When can split $E(Y)$ into two parts based on whether the event $X \le m$ occurs 

$$
\begin{split}
E(Y) &= E(Y | X \le m)P(X \le m) +E(Y | X > m)P(X \gt m) \\
&\ge (a - m)P(X \le m) + (m - a)P(X > m) \\
&= (a-m)P(X \le m) - (a - m)(1 - P(X \le m)) \\
&= (a - m)(2P(X \le m) - 1)
\end{split}
$$
Since for median $m$ we know $P(X \le m) \le \frac{1}{2}$, we get $E(Y) \ge 0$ with equality when $a = m$. This means the mean absolute error $E|X - a|$ is minimized when $a$ is the median of $X$. 


## MGF


\BeginKnitrBlock{theorem}\iffalse{-91-77-111-109-101-110-116-115-32-118-105-97-32-100-101-114-105-118-97-116-105-101-115-32-111-102-32-77-71-70-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:mgf-moment"><strong>(\#thm:mgf-moment)  \iffalse (Moments via derivaties of MGF) \fi{} </strong></span>The $n$th momment of r.v. $X$ is the $n$th derivative of its MGF evaluated at zero

$$
E(X^n) = M^{n}(0)
$$</div>\EndKnitrBlock{theorem}

\BeginKnitrBlock{proof}<div class="proof">Proof</div>\EndKnitrBlock{proof}

The Taylor expansion of $M(t)$ about $0$ is

$$
M(t) = \sum_{n=1}^{\infty} M^{(n)}(0) \frac{t^n}{n!}
$$

On the other hand, use the fact that the Taylor expansion of $e^x$ about $0$ is $\sum \frac{x^n}{n!}$, we have

 

$$
\begin{split}
M(t)  &= E(e^{tX}) \\
&= E(\sum_{n = 0}^{\infty} \frac{X^nt^n}{n!}) \\
&= \sum_{n = 0}^{\infty} E(X^n)\frac{t^n}{n!} \qquad \text{due to techinical conditions of MGF}\\ 
\end{split} 
$$

Matching the coefficients of the two expansions, we get $E(X^n) = M^{(n)}(0)$

Note that expectation of infinite sum $E(\sum_{i = 0}^{\infty}X_i)$ may not be equal to $\sum_{n=0}^{\infty}E(X_I)$. In other words, linearity of expectation may not hold for infinite sums. However, the definition of MGF has a technical condition -- MGF is finite on some open interval $(-a, a)$ containing $0$ -- which ensures the linearity property used in the following formula.  


\BeginKnitrBlock{theorem}\iffalse{-91-79-110-101-45-116-111-45-111-110-101-32-114-101-108-97-116-105-111-110-115-104-105-112-32-98-101-116-119-101-101-110-32-77-71-70-32-97-110-100-32-100-105-115-116-114-105-98-117-116-105-111-110-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:mgf-distribution"><strong>(\#thm:mgf-distribution)  \iffalse (One-to-one relationship between MGF and distribution) \fi{} </strong></span>The MGF of a random variable determines its distribution. If two random variables have the same MGF, then they follow the same distribution. </div>\EndKnitrBlock{theorem}

\BeginKnitrBlock{theorem}\iffalse{-91-77-71-70-32-97-110-100-32-99-111-110-118-111-108-117-116-105-111-110-115-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:mgf-convolution"><strong>(\#thm:mgf-convolution)  \iffalse (MGF and convolutions) \fi{} </strong></span>The MGF of the convolution (sum) of two independent r.v. $X$ and $Y$, is the product of the individual MGFs. This is because 

</div>\EndKnitrBlock{theorem}

$$
\begin{split}
M_{X + Y}(t) &= E(e^{t(X + Y)}) \\
&= E(e^{tX} \cdot e^{tY})\\
&= E(e^{tX}) \cdot E(e^{tY}) \qquad \text{X and Y are independent}\\
&= M_X(t) \cdot M_Y(t)
\end{split}
$$
