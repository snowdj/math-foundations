
# (PART) Linear Algebra {-}


# Basic Matrix Algebra






## Matrix Multiplication

A common way of looking at matrix-vector multiplication $A\bar{x}$ is to think of as a linear combination of column vectors in $A$:  

$$
\begin{aligned}
A\bar{x} &= [\bar{a}_1 \;\; \cdots \;\; \bar{a}_n] 
\begin{bmatrix}
x_1 \\
\vdots \\
x_n
\end{bmatrix} \\
&= x_1\bar{a}_1 + \cdots + x_n\bar{a}_n
\end{aligned}
$$


Likewise, for any $\bar{x}^{T} = [x_1, \cdots, x_n]^T$ and matrix $A_{m \times n}$, $x^{T}A$ can be thought of as a linear combination of rows in $A$ to produce a new row vector: 

$$
[x_1 \;\; \cdots \;\; x_n] 
\begin{bmatrix}
\bar{a}_1^T \\
\vdots  \\
\bar{a}_n^T
\end{bmatrix} 
= x_1\bar{a}_1^T + \dots + x_n\bar{a}_n^T
$$
For matrix-matrix multiplication $AB$, besides the dot product definition we can see it as **column row expansion**.  

<br>

(ref:cr-expansion) Column-row expansion of $AB$

\BeginKnitrBlock{theorem}\iffalse{-91-40-114-101-102-58-99-114-45-101-120-112-97-110-115-105-111-110-41-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:cr-expansion"><strong>(\#thm:cr-expansion)  \iffalse ((ref:cr-expansion)) \fi{} </strong></span>
if $A$ is $m \times n$ and $B$ is $n \times p$, then 

$$
\begin{aligned}
AB &= [\text{col}_1(A) \cdots \text{col}_n(A)] 
\begin{bmatrix}
\text{row}_1(B) \\
\vdots \\ 
\text{row}_n(B)
\end{bmatrix} \\ 
&= \text{col}_1(A)\text{row}_1(B) + \cdots +  \text{col}_n(A)\text{row}_n(B)
\end{aligned}
$$</div>\EndKnitrBlock{theorem}



Note that each $\text{col}_1(A)\text{row}_1(B)$ is a rank 1 $m \times p$ matrix. 


The following subsections follows Chapter 7 of VMLS [@boyd2018introduction], introducing  some special matrices and their effect in matrix multiplication.  


### Geometric Transformations 

**scaling**


**dilation**

**rotation**

$$
\begin{bmatrix}
\cos\theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{bmatrix}
\begin{bmatrix}
\rho \cos\alpha \\ 
\rho \sin\alpha 
\end{bmatrix} =
\begin{bmatrix} 
\rho(\cos\theta\cos\alpha - \sin\theta\sin\alpha) \\
\rho(\sin\theta \cos\alpha + \cos \theta \sin\alpha)
\end{bmatrix}
= 
\begin{bmatrix}
\rho \cos(\theta + \alpha) \\
\rho \sin(\theta + \alpha)
\end{bmatrix}
$$

**reflection**


### Matrix Multiplication as Linear Transformation

They are matrices whose multiplication effect do that fall into specific geometric categories like scaling, dilation, and rotation. They do, in some sense, exert the same type of influence on vectors through multiplication. 

It turns out that another way to look at $A_{m \times n} \, x _{ n \times 1} = b_{m \times 1}$, besides linear combination of column vectors, is to think of the matrix $A$ as an force that “acts” on a vector $x$ in $\mathbb{R^n}$ by multiplication to produce a new vector called $b$ in $\mathbb{\mathbb{R^m}}$.  

A transformation $T$ from $\mathbb{R^n}$ to $\mathbb{R^m}$ is a rule that assigns each vector \bar{x} in $\mathbb{R^n}$ a vector $T(x)$ in $\mathbb{R^m}$, which is called the **image** of \bar{x} (under the action of $T$). 

It can be show that such transformations induced by multiplying a matrix is a type of **linear transformation**, because it satisfies all required properties to be linear:  

$$
\begin{aligned}
\text{vector addition} \quad A(\bar{u} + \bar{v}) &= A\bar{u} + A\bar{v}  \\ 
\text{scalar multiplication} \quad A(c\bar{u}) &= cA\bar{u}
\end{aligned}
$$
<hr>

\BeginKnitrBlock{theorem}\iffalse{-91-108-101-102-116-32-109-117-108-116-105-112-108-105-99-97-116-105-111-110-32-97-115-32-108-105-110-101-97-114-32-116-114-97-110-115-102-111-114-109-97-116-105-111-110-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-1"><strong>(\#thm:unnamed-chunk-1)  \iffalse (left multiplication as linear transformation) \fi{} </strong></span>There is a one to one relationship between a linear transformation and a matrix. Let $T: \mathbb{R^n} \rightarrow \mathbb{R^m}$ be a linear transformation. Then there exists a **unique** matrix $A$ such that:  
  
$$
T(\bar{x}) = A\bar{x} \quad \text{for all} \; x \; \text{in} \; \mathbb{R^n}  
$$
  
In fact, $A$ is a $m \times n$ matrix whose $j$th column is the vector $T(\bar{e}_j)$, where $\bar{e}_j$ is the $j$th basis of $\mathbb{R}^n$ </div>\EndKnitrBlock{theorem}

::: {.pr}
$$
\bar{x} = x_1\bar{e}_1 + \dots + x_n{\bar{e}_n}
$$
And because $T(\bar{x})$ is a linear transformation: 

$$
\begin{split}
T(\bar{x}) &= x_1T(\bar{e}_1) + \dots + x_nT(\bar{e}_n) \\
&= [T(\bar{e}_1) \, \cdots \, T(\bar{e}_n)]\bar{x} \\
&= (A\bar{x})_{m \times 1}
\end{split}
$$
:::



In other words, the transformation is determined once we know what all basis in $\mathbb{R}^n$ become in $\mathbb{R}^m$.

The matrix $A$ is called the **standard matrix for the linear transformation** $T$.  

<hr>

(ref:onto) A mapping is onto $\mathbb{R^m}$

\BeginKnitrBlock{definition}\iffalse{-91-40-114-101-102-58-111-110-116-111-41-93-}\fi{}<div class="definition"><span class="definition" id="def:unnamed-chunk-2"><strong>(\#def:unnamed-chunk-2)  \iffalse ((ref:onto)) \fi{} </strong></span>A mapping $T: \mathbb{R^n} \rightarrow \mathbb{R^m}$ is said to be **onto** \mathbb{R^m} if each $\bar{b}$ in $\mathbb{R^m}$ is the image of at least one $\bar{x}$ in \mathbb{R^n}</div>\EndKnitrBlock{definition}

Equivalently, $T$ is onto $\mathbb{R^m}$ means that there exists at least one solution of $T(\bar{x}) = \bar{b}$ for any $\bar{b}$ in $\mathbb{R}^m$

<br>

\BeginKnitrBlock{definition}\iffalse{-91-111-110-101-45-116-111-45-111-110-101-32-109-97-112-112-105-110-103-93-}\fi{}<div class="definition"><span class="definition" id="def:unnamed-chunk-3"><strong>(\#def:unnamed-chunk-3)  \iffalse (one-to-one mapping) \fi{} </strong></span>

A mapping T: $\mathbb{R^n} \rightarrow \mathbb{R^m}$ is said to be **one-to-one** if each $\bar{b}$ in $\mathbb{R^m}$ is the image of *at most* one $\bar{x}$ in $\mathbb{R^n}$</div>\EndKnitrBlock{definition}

Equivalently, $T$ is one-to-one if, for each $\bar{b}$ in $\mathbb{R^m}$, the equation $T(\bar{x}) = \bar{b}$ has either a unique solution or none at all.   

<br>

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-4"><strong>(\#thm:unnamed-chunk-4) </strong></span>Let $\mathbb{R}^n \rightarrow \mathbb{R}^m$ be a linear transformation, and $A$ the standard matrix. Then 

- $T$ maps $mathbb{R}^n$ onto $\mathbb{R}^m$ if only if columns of $A$ span $\mathbb{R}^m$  

- $R$ is one-to-one if and only if columns of $A$ are linearly independent </div>\EndKnitrBlock{theorem}


### Selector Matrix 

Let the standard basis in $\mathcal{R}^n$ be 

$$
\begin{aligned}
\bar{e}_1^T  &= [1, 0, \cdots, ..., 0] \\
\bar{e}_2^T  &= [0, 1, \cdots, ..., 0] \\
& \vdots  \\
\bar{e}_n^T  &= [0, 0, \cdots, ..., 1] 
\end{aligned}
$$

Then an $m \times n$ matrix $A$ formed by a subset of such vectors are called a selector matrix. In other words, an $m \times n$ selector matrix $A$ is one in which each row is a standard unit vector 

$$
A = \begin{bmatrix}
\bar{e}_{k_1}^T \\ 
\vdots \\
\bar{e}_{k_m}^T
\end{bmatrix}
$$

where $1 \le k_1, ..., k_m \le n$. When a selector matrix multiplies a vector $\bar{x}$, it returned the $k_i$th entry of $\bar{x}$ on the $i$th entry of $y = A\bar{x}$. For example, we can construct a $4 \times n$ selector matrix

$$
A = 
\begin{bmatrix}
\bar{e}_2^T \\
\bar{e}_1^T \\ 
\bar{e}_5^T \\ 
\bar{e}_8^T
\end{bmatrix}
$$
When multiplying $\bar{x}$

$$
\begin{bmatrix}
\bar{e}_2^T \\
\bar{e}_1^T \\ 
\bar{e}_5^T \\
\bar{e}_8^T
\end{bmatrix}
\begin{bmatrix}
x_1 \\
\vdots \\ 
x_n 
\end{bmatrix}
= 
\begin{bmatrix}
x_2 \\
x_1 \\
x_5 \\
x_8
\end{bmatrix}
$$
The identity matrix, and the reverser matrix 

$$
A = 
\begin{bmatrix}
\bar{e}_n^T \\ 
\vdots \\
\bar{e}_1^T
\end{bmatrix}
= 
\begin{bmatrix}
0 & 0 & \cdots & 0 & 1 \\
0 & 0 & \cdots & 1 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
1 & 0 & \cdots & 0 & 0
\end{bmatrix}
$$
are one of the selector matrices family. 

Selector matrices have important applications in down-sampling, image cropping, and permutation. (P.144, VSLM) 


### Discrete Convolution

The (discrete) *convolution* of an $n$-vector $a$ $a$ and $m$-vector $b$ is a $(n + m - 1)$-vector, denoted $a * b$, with entries

$$
c_k = \sum_{i + j = k + 1}a_ib_j, \quad k = 1, ..., n + m - 1
$$

For example, the convolution of $n = 5$ and $m = 3$ is 

$$
\begin{aligned}
c_1 &= a_1b_1 \\
c_2 &= a_1b_2 + a_2b_1  \\
c_3 &= a_1b_3 + a_2b_2 + a_3b_1 \\
c_4 &= a_2b_3 + a_3b_2 + a_4b_1 \\
c_5 &= a_3b_3 + a_4b_2 + a_5b_1 \\
c_6 &= a_4b_3 + a_5b_2 \\
c_7 &= a_5b_3
\end{aligned}
$$
A important application of convolution arises in polynomial multiplication. If $a$ and $b$ represent coefficients of two polynomials 

$$
p(x) = a_1 + a_2x + \cdots + a_nx^{n-1}, \quad q(x) = b_1 + b_2x + \cdots + b_mx^{m - 1}
$$
then the coefficients of the product polynomial $p(x)q(x)$ are represented by $c = a * b$ 

$$
p(x)q(x) = c_1 + c_2x + \cdots + c_{n + m - 1}x^{n + m - 2}
$$
With this interpretation using polynomial multiplication, we can quickly verify some properties of convolution 

- symmetric $a * b = b * a$  

- associative $(a * b) * c = a * (b * c)$   

- $a * b = 0$ if and only if one of $a$ and $b$ are zero vectors. 

How is convolution related to matrix multiplication. A basic fact is that for a fixed $a$, $a * b$ is a linear function of $b$, and likewise for $b$. This mean $a * b$ can be expressed as a matrix-vector product 

$$
a * b = T(b)a = T(a)b
$$

According to the relationship between matrix multiplication and linear transformation, we conclude that $T(b)$ and $T(a)$ are matrices that are determined and constructed by the elemetns of $b$ and $a$ respectively. 

Refer to the previous example, we have

$$
T(b) = 
\begin{bmatrix}
b_1 & 0 & 0 & 0 & 0 \\
b_2 & b_1 & 0 & 0 & 0 \\
b_3 & b_2 & b_1 & 0 & 0 \\
0 & b_3 & b_2 & b_1 &0 \\
0 & 0 & b_3 & b_2 & b_1 \\
0 & 0 & 0 & b_3 & b_2 \\
0 & 0 & 0 & 0 & b_3 
\end{bmatrix},
\quad 
T(a) = 
\begin{bmatrix}
a_1 & 0 & 0 \\
a_2 & a_1 & 0 \\
a_3 & a_2 & a_1 \\
a_4 & a_3 & a_2 \\
a_5 & a_4 &  a_3 \\
0 & a_5 & a_4 \\
0 & 0 & a_5
\end{bmatrix}
$$

$T(a)$ and $T(b)$ both have the same values along any diagonal, a property characterizing the so-called *Toeplitz* matrices. 

Convolution has computational applications in areas like time series smoothing, first order differences and audio filtering. (P. 150, VMLS)


## Elemetary matrix and row operations  

An *elementary matrix* is one that is obtained by performing a single elementary row
operation on an identity matrix $I$. Each elementary matrix $E$ is invertible. The inverse of $E$ is the elementary matrix of the same type that transforms $E$ back into $I$.  

Left multiplication by a elementary matrix has a nice illustration. There are 3 primary types of elementary matrices (example for $3 \times 3$):  

$$
E_1 = 
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
-4 & 0 & 1
\end{bmatrix} 
,\;
E_2 = 
\begin{bmatrix}
0 & 1 & 0 \\
1 & 0 & 0 \\
0 & 0 & 1
\end{bmatrix} 
,\;
E_3 = 
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 5
\end{bmatrix} 
$$
$E_1, E_2, E_3$ represents 3 types of elementary row operations applicable to a $3 \times 3$ matrix, 

(1) *Row addition*, a scalar multiple of the $i$th row is added to the $j$th row

(2) *Row interchange*, the $i$th row and the $j$th row of the matrix are interchanged  

(3) *Row scaling*, the $i$th row is multiplied by a scalar. 

$$
\begin{aligned}
E_1A &= 
\begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
- 4a_{11} + a_{31} & -4a_{12} + a_{32} & -4a_{13} + a_{33}
\end{bmatrix}  \\ \\  
E_2A &= 
\begin{bmatrix}
a_{21} & a_{22} & a_{23} \\
a_{11} & a_{12} & a_{13} \\
a_{31} & a_{32} & a_{33}
\end{bmatrix} \\ \\
E_3A &= 
\begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
5a_{31} & 5a_{32} & 5a_{33} \\
\end{bmatrix}
\end{aligned}
$$
Thus, any row operation on $A$ is equivalent to left multiply a corresponding elementary matrix $E$.  


Since row operation are invertible, elementary matrices are invertible. This gives a general way of finding the inverse matrix of $A$.  

\BeginKnitrBlock{theorem}\iffalse{-91-97-110-32-97-108-103-111-114-105-116-104-109-32-102-111-114-32-102-105-110-100-105-110-103-32-105-110-118-101-114-115-101-32-109-97-116-114-105-99-101-115-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:find-inverse"><strong>(\#thm:find-inverse)  \iffalse (an algorithm for finding inverse matrices) \fi{} </strong></span>Row reduce the augmented matrix $[A \;\; I]$, when $A$ becomes $I$, $I$ becomes $A^{-1}$. Otherwise $A^{-1}$ is not invertible. </div>\EndKnitrBlock{theorem}





## LU Factorization 

https://fml-fam.github.io/blog/2020/07/03/matrix-factorizations-for-data-analysis/

A *factorization* of matrix $A$ is an equation that expresses $A$ as a product of two or more matrices.  


\BeginKnitrBlock{definition}\iffalse{-91-76-85-32-102-97-99-116-111-114-105-122-97-116-105-111-110-93-}\fi{}<div class="definition"><span class="definition" id="def:unnamed-chunk-5"><strong>(\#def:unnamed-chunk-5)  \iffalse (LU factorization) \fi{} </strong></span>Suppose $A$ can be reduced to an echelon form $U$ **using only row addition and row scaling**, there exist a set of unit lower trangular matrices $E_1, \dots, E_p$ such that 

$$
E_p \cdots E_1A = U  
$$
  
Then 

$$
A = (E_p \cdots E_1)^{-1}U = LU
$$

where $u$ is a the upper triangular row echelon form (or upper trapezoidal), and $L$ an lower triangular matrix
$$
L = (E_p \cdots E_1)^{-1}  
$$</div>\EndKnitrBlock{definition}

LU decomposition expresses a matrix (don't have to be square or invertible) as the product of a square lower triangular matrix $L$ and a rectangular upper triangular matrix $U$.  

From the definition, we know that row operations on $A$ must only be confined to *row addition* and *row scaling*, but not *row interchange*. Otherwise $(E_p \cdots E_1)^{-1}$ cannot be lower triangular. The most common needs for row exchanges in row reduction is when $a_{11}$ is 0. For example, the following matrix does not have a LU factorization because it first requires exchanging two rows to produce row echelon form ^[In particular, a non-singular matrix with $a_{11} = 0$ cannot have LU decomposition]  

$$
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}
$$

To give a former definition of LU factorization, one can show that if all **principal submatrices are non-singular**^[square matrices whose diagonal entries are those of the original matrix], then the factorization exists. Note that this condition is **not necessary**, the following matrix has a zero in (2, 2) position violating the rule, but it can still be expressed in terms of LU

$$
\begin{bmatrix}
2 & 1 & 0 \\
1 & 0 & 0 \\
1 & 1 & 1
\end{bmatrix}
= 
\begin{bmatrix}
2 & 0 & 0 \\
1 & -\frac{1}{2} & 0 \\
1 &  \frac{1}{2} & 1
\end{bmatrix}
\begin{bmatrix}
1 & \frac{1}{2} & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$

If an LU factorization exists, we shall notice that the LU form is "asymmetric" on the diagonal, in the sense that L has all $1$s and $U$ has the pivots. We can factor out another diagonal matrix $D$ to also have all $1$s on $U$'s diagonal  

$$
U = \begin{bmatrix}
d_{1} \\
& d_{2} \\
& & \ddots \\ 
& & & d_n
\end{bmatrix}
\begin{bmatrix}
1 & u_{12} / d_1 & \cdots & u_{1n}/d_1 \\
& 1 & \cdots & u_{2n}/d_2 \\
& & \ddots & \vdots \\
& & & 1
\end{bmatrix}
$$

Then the $LU$ factorization becomes $A = LDU$, where $L$ and $U$ have ones on its diagonal and $D$ is the diagonal matrix of pivots. 

<hr> 

In cases where row exchanges are needed to produce the echelon form, we can express the elimination process in terms of a permutation matrix $P$ and the other set of row addition operations, defined by $L_1, ..., L_{k}$  

$$
PL_{k}\cdots L_1A = U
$$

Note that permutation matrix $P$ satisfies $PP^T = I$. Multiplying both sides with $P^T$ and the inverses of $L_1, ..., L_{k}$, we obtain 

$$
A = \underbrace{ L_1^{-1} \cdots L_k^{-1}}_{L}P^TU
$$
One can try to polish this form  by obtain a decomposition in which the permutation matrix occurs before the lower triangular matrix $L$ ($L$ and $P$ are not the same after reordering)  

$$
A = P^TLU
$$

It's also common to write this decomposition as $PA = LU$.

## Determinants

In the $2 \times 2$ case, the determinant of $A$ is simply 

$$
\begin{vmatrix}
a & b \\
c & d \\
\end{vmatrix}
= ad - bc
$$

When $A$ is $3 \times 3$,  we still get a not-too-messy explicit formula to compute its determinant 

$$
\begin{vmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33}
\end{vmatrix}
= a_{11}a_{22} a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21} a_{32}  - a_{13}a_{22}a_{31} - a_{12}a_{21} a_{33} - a_{11}a_{23}a_{32} 
$$

This is the sum of products on the foward diagonal minus the sum of products on the backward diagonal. 

### Cofactor Expansion

Cofactor expansion is a more practical way to compute determinant of bigger matrices. The $(i, j)\text{-cofactor}$ of $A$ is a number $C_{ij}$ in $\mathbb{R}$ given by 

$$
C_{ij} = (-1)^{i + j} \det A_{ij}
$$
where $A_{ij}$ denotes the submatrix formed by deleting the $i$h row and $j$th column of $A$. 

\BeginKnitrBlock{theorem}\iffalse{-91-99-111-102-97-99-116-111-114-32-101-120-112-97-110-115-105-111-110-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:cofactor-expansion"><strong>(\#thm:cofactor-expansion)  \iffalse (cofactor expansion) \fi{} </strong></span>The determinant of an $n \times n$ matrix is given by a **cofactor expasion** across any row or column. For example, the expansion across the $i$th row is:  

$$
\det A = a_{i1}C_{i1} + a_{i2}C_{i2} + \cdots + a_{in}C_{in} 
$$
  
and cross the $j$th column is 

$$
\det A = a_{1j}C_{1j} + a_{2j}C_{2j} + \cdots + a_{nj}C_{nj} 
$$</div>\EndKnitrBlock{theorem}




### Geometric Interpretation of Determinant 

Given matrix $A_{n \times n}$  

$$
\begin{bmatrix}
a_1^{T} \\
a_2^{T} \\
\vdots \\
a_n^{T}
\end{bmatrix}
$$
where $a_1, ..., a_n$ are row vectors of A. Then $|\det A|$ is the volume of parallelotope constrained by $a_1, ..., a_n$. When $A$ is $2\times2$, $|\det A|$ is simply the area of the parallelogram defined by two side $a_1, a_2$


### Properties of Determinant 

A list of arithmetic properties of determinants, A is an $n\times n$ matrix: 

1. $\det(A^T) = \det(A)$
2. $\det(kA) = k^n \det(A)$
3. $\det(AB) = \det(A)\det(B)$ (although $AB \not = BA$ in general), it follows that  $\det(A^n) = \det(A)^n$  
4. $\det(A^{-1}) = 1 / \det(A)$, if $A$ is invertible
5. determinant is equal to the product of eigenvalues (counting multiplicity) $\det(A)  = \prod_{i=1}^n{\lambda_i}$  
6. If the $i$-th row (column) in A is a sum of the $i$-th row (column) of a matrix $B$ and the $i$-th row (column) of a matrix $C$ and all other rows in $B$ and $C$ are equal to the corresponding rows in $A$ (that is, $B$ and $C$ differ in one row only), then $\det(A)=\det(B)+\det(C)$. This can be proven by cofactor expansion across the $i$th row. The same applies to columns. 

Row operations on $A$ has the following effect on $\det A$

- if we multiply a single row in $A$ by a scalar $k \in \mathbb{R}$, then the determinant of the new matrix is $k\det A$  

- if we exchange two rows $a_i^T$ and $a_j^T$ of $A$, determinant becomes $-\det A$ 

- Add a multiple of one row to another row has **no** effect on determinant 


Note that all row operations don't change whether or not a determinant is 0, only change it by a non-zero factor or change its sign.  



The first two effects can be easily understood in connection with geometric meaning of determinant. What third property means is illustrated by the following example. Represent $B$ and $C$ with row vectors

$$
B = 
\begin{bmatrix}
a_1^T \\ 
\vdots \\
a_i^T \\
\vdots \\
a_j^T \\ 
\vdots \\
a_n^T
\end{bmatrix}
,
C  = 
\begin{bmatrix}
a_1^T \\ 
\vdots \\
 ka_j^T \\
\vdots \\
a_j^T \\ 
\vdots \\
a_n^T
\end{bmatrix}
$$
And define $A$ as

$$
A = 
\begin{bmatrix}
a_1^T \\ 
\vdots \\
a_i^T + ka_j^T \\
\vdots \\
a_j^T \\ 
\vdots \\
a_n^T
\end{bmatrix}
$$
It is obvious that here $A$ is on purpose the result of $B$ after performing row addition (add a multiple of the $j$th row to the $i$th row). And by property 6 $\det(A) = \det(B) + \det(C)$.  Also in this case, $C$ has determinant $0$, and this property indeed proves that row addition does not change determinant. In more general cases, $|C|$ definitely does not have to be zero.




### Cramer's Rule

Given an $n \times n$ matrix $A$ and $\bar{b}$ in $\mathbb{\mathbb{R^n}}$, denote $A_i(\bar{b})$ as the matrix derived by $A$ by **replacing** column $i$ by vector $\bar{b}$:  

$$
A_i(\bar{b}) = [\bar{a}_1 \cdots \underbrace{\bar{b}}_{\text{column} \,i} \cdots \bar{a}_n]
$$

\BeginKnitrBlock{theorem}\iffalse{-91-67-114-97-109-101-114-39-115-32-114-117-108-101-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:cramer"><strong>(\#thm:cramer)  \iffalse (Cramer's rule) \fi{} </strong></span>Let $A$ be an invertible $n \times n$ matrix. For any $\bar{b}$ in $\mathbb{R^n}$, the unique solution $\bar{x}$ of $A\bar{x} = \bar{b}$ has entries given by: 

$$
x_i = \frac{\det A_i(\bar{b})}{\det A}
$$</div>\EndKnitrBlock{theorem}


## Trace


The *trace* of square matrix $A$ is the sum of its diagonal entries $\sum_{i = 1}^{n}A_{ii}$.  

The trace has the following properties:  

1. $\text{tr}(A + B) = \text{tr}(A) + \text{tr}(B)$  
2. $\text{tr}(kA) = k\,\text{tr}(A)$, $k$ is a scalar     
3. $\text{tr}(A^T) = \text{tr}(A)$  
4. For $A$, $B$ such that $AB$ is square, $\text{tr}(AB) = \text{tr}(BA)$  
5. Trace of product of multiple matrices is invariant to *cyclic permutations*, $\text{tr}(ABC) = \text{tr}(BCA) = \text{tr}(CAB)$. Note that the reordering cannot be done arbitrarily, fro example $\text{tr}(ABC) \not= \text{tr}(ACG)$ in general. 
6. Trace is equal to the sum of its eigenvalues (repeated according to multiplicity) $\text{tr}(A) = \sum_{i = 1}^n{\lambda_i}$  
7. $\text{tr}(\bar{a}\bar{a}^T) = \bar{a}^T\bar{a}$


## Matrix Inversion

\BeginKnitrBlock{rmdnote}<div class="rmdnote">Note that the inverse of a matrix is only defined for square matrces, so is determinants in Section \@ref(determinants). 

In practice $A^{-1}$ is seldom computed, because computing both $A^{-1}$ and $A^{-1}\bar{b}$ to solve linear equations takes about 3 times as many arithmetic operations as solving $A\bar{x} = \bar{b}$ by row reduction.</div>\EndKnitrBlock{rmdnote}

Assume that $A$ and $B$ are both non-singular
\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-7"><strong>(\#thm:unnamed-chunk-7) </strong></span>If A and B are both invertible matrces, we have

$$
(A^{-1})^{-1} = A  
$$
  
$$
(AB)^{-1} = B^{-1}A^{-1}
$$

$$
(A^T)^{-1} = (A^{-1})^T
$$</div>\EndKnitrBlock{theorem}



In Section \@ref(thm:find-inverse), we derive an algorithm of finding inverse matrices by row reductions on the augmented matrix $[A \; | \; I]$. However, Cramer's rule \@ref(thm:cramer) leads to a general formula of calculating  $A^{-1}$, if it exists.  

The $j$th column of $A^{-1}$ is a vector $\bar{x}$ that satisfies:  

$$
A\bar{x} = \bar{e}_j
$$
By Cramer's rule 
$$
\{(i,j) \text{ entry of } A^{-1}\} = x_i = \frac{\det A_i{(\bar{e}_j)}}{\det A}
$$

A cofactor expansion \@ref(thm:cofactor-expansion) down column $i$ of $A_i{(\bar{e}_j)}$ shows that:   

$$
\det A_i{(\bar{e}_j)} = (-1)^{i + j}\det A_{ji} = C_{ji}
$$
where $C_{ji}$ is a cofactor of $A$. Note that the ($i$, $j$)th entry of $A^{-1}$ is the cofactor $C_{ji}$ divided by $\det A$ (the subscript is reversed). Thus


\begin{equation}
(\#eq:inverse-adjugate)
A^{-1} = \frac{1}{\det A} 
\begin{bmatrix}
C_{11} & C_{21} & \cdots & C_{n1} \\ 
C_{12} & C_{22} & \cdots & C_{n2} \\
\vdots & \vdots & & \vdots \\
C_{1n} & C_{2n} & \cdots & C_{nn} \\
\end{bmatrix}
\end{equation}

The right side of Eq \@ref(eq:inverse-adjugate) is called the *adjugate* of $A$, often denoted by $\text{adj}\, A$.  

\BeginKnitrBlock{theorem}\iffalse{-91-65-110-32-73-110-118-101-114-115-101-32-70-111-114-109-117-108-97-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-8"><strong>(\#thm:unnamed-chunk-8)  \iffalse (An Inverse Formula) \fi{} </strong></span>Let $A$ be an invertible $n \times n$ matrix. Then 

$$
A^{-1} = \frac{1}{\det A}\text{adj}\, A
$$</div>\EndKnitrBlock{theorem}

<hr> 

Interestingly, theorem \@ref(thm:cayley-hamilton) in later chapters shows that for invertible matrix $A$, its inverse $A^{-1}$ can be represented as a polynomial of $A$.


### The Matrix Inversion Lemma




\BeginKnitrBlock{lemma}\iffalse{-91-84-104-101-32-77-97-116-114-105-120-32-73-110-118-101-114-115-105-111-110-32-76-101-109-109-97-93-}\fi{}<div class="lemma"><span class="lemma" id="lem:matrix-inversion-lemma"><strong>(\#lem:matrix-inversion-lemma)  \iffalse (The Matrix Inversion Lemma) \fi{} </strong></span>Let $A$ be an invertible $n \times n$ square matrix, and $\bar{v}$ and $\bar{u}$ be d-dimensional vectors. Then, $A + \bar{u}\bar{v}^T$ is invertible if and only if $\bar{v}^TA\bar{u} \not = -1$. In such a case, the inverse formula is given by 

$$
(A + \bar{u}\bar{v}^T) = A^{-1} - \frac{A^{-1}\bar{u}\bar{v}^TA^{-1}}{1 + \bar{v}^TA^{-1}\bar{u}}
$$</div>\EndKnitrBlock{lemma}


<hr>

\BeginKnitrBlock{theorem}\iffalse{-91-87-111-111-100-98-117-114-121-32-73-100-101-110-116-105-116-121-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:woodbury"><strong>(\#thm:woodbury)  \iffalse (Woodbury Identity) \fi{} </strong></span>Let $A$ be an invertible $n \times n$ square matrix, and $U, V$ nonzero $n \times k$ matrices  for some small values of $k$. Then, $A + UV^T$ is invertible if and only if the $k \times k$ amtrix $(I +V^TA^{-1}U)$ is invertible. In such a case, the inverse formula is given by 

$$
(A + UV)^{-1} = A^{-1} - A^{-1}U(I + V^TA^{-1}U)^{-1}V^TA^{-1}
$$</div>\EndKnitrBlock{theorem}

It's easy to find that the Woodbury Identity is an extension of the matrix inversion lemma, where $\bar{u} \rightarrow U$ and $\bar{v} \rightarrow V$.




<hr>

\BeginKnitrBlock{proposition}<div class="proposition"><span class="proposition" id="prp:unnamed-chunk-9"><strong>(\#prp:unnamed-chunk-9) </strong></span>For square matrix $P$ (**not** assuming invertible), if $I + P$ is invertible, then $(I + P)^{-1}$ satisfies:  

$$
(I + P)^{-1} = I - (I + P)^{-1}P
$$</div>\EndKnitrBlock{proposition}

As a quick check, right and left multiply $(I + P)$ to see if we get an identity. 

$$
\begin{split}
(I + P)^{-1}(I + P) &= I \\
&= \Big(I - (I + P)^{-1}P \Big )(I + P) \\
&= I + P -(1 + P)^{-1}P(I + P) \\
&= (I + P)( I - (I + P)^{-1}P) \\
&= (I + P)(I + P)^{-1}\\
&= I
\end{split}
$$
and left multiply

$$
\begin{split}
(I + P)(I + P)^{-1} &= I \\
&= (I + P)(I - (I + P)^{-1}P) \\
&= I + P - P\\
&= I
\end{split}
$$
<hr> 


\BeginKnitrBlock{proposition}\iffalse{-91-80-117-115-104-32-84-104-114-111-117-103-104-32-73-100-101-110-116-105-116-121-93-}\fi{}<div class="proposition"><span class="proposition" id="prp:push-through-identity"><strong>(\#prp:push-through-identity)  \iffalse (Push Through Identity) \fi{} </strong></span>Let $U$ and $V$ be $m \times n$ matrices, we have 

$$
U^T(I + VU^T)^{-1} = (I + U^TV)^{-1}U^T
$$
The above result shows the following for any $m \times n$ matrix $A$ and any scalar $\lambda > 0$ 

$$
A^T(\lambda I + AA^T)^{-1} = (\lambda I + A^TA)^{-1}A^T
$$</div>\EndKnitrBlock{proposition}








## Complexity of Matrix Computation

This chapter concludes with a summary of complexity (number of flops needed) in common matrix computations.


An $m \times n$ matrix is often represented by an $m \times n$ array of floating numbers in a computer, requiring $8mn$ bytes (8 bytes for one element). In the case of a sparse matrix, we can store only the nonzero entries with row index $i$ (integer), column index $j$ (integer) and its value $A_{ij}$ (floating point). Let $\text{nnz}(A)$ be the number of nonzero entries, since we only need 4 bytes to store a integer, storing a sparse matrix requires roughly $16\text{nnz}(A)$ bytes. 


Let $A$ be an $m \times n$ matrix, and other matrices / vectors be of conformable size for arithmetic operations. The complexity (approximate number of flops) of common matrix operations are listed below 

|Operation|Expression|Complexity|Explanation|
|:-:|:-:|:-:|:-:|
|matrix addition|$A + B$|$mn$ <br> and $\min(\text{nnz}(A), \text{nnz}(B))$ if one of $A$ and $B$ is sparse|For any entry $i,j$ for which one of $A_{ij}$ and $B_{ij}$ is zero, no arithmetic operations are needed to find  $(A + B)_{ij}$|
|scalar multiplication|$kA$|$mn$ <br> $\text{nnz}(A)$ when $A$ is sparse||
|matrix-vector multiplication|$A\bar{x}$|$m(2n - 1)$|equivalent to $m$ inner products between rows of $A$ and $\bar{x}$|
|matrix-vector multiplication when $A$ is sparse|between $\text{nnz}(A)$ and $2\text{nnz}(A) - 1$|$A\bar{x}$|First we need $\text{nnz}(A)$ multiplications, and certain number of additions. We need most additions when nonzero entries are arranged next to each other, and least when they are separated in different columns and rows (for example for diagonal matrix $A$, we need no additions at all)|
|matrix-matrix multiplication|$A_{m \times n}B_{n \times p}$|$2mnp$|$2n - 1$ for each inner product between rows of $A$ and columns of $B$, with $m \times p$ inner products in total, which is roughly $2mnp$ flops|
|sparse matrix multiplication|$AB$|no more than $2\min\{\text{nnz}(A)p, \text{nnz}(B)m\}$|Suppose $A$ is sparse $m \times n$, and $B$ is normal $n \times p$. Then the inner product of the $i$th row $\bar{a}_i^T$ and the $j$th column of $B$ requires no more than $2\text{nnz}(\bar{a}_i^T)$ flops. That adds up to $2\text{nnz}(A)p$ in total. If $B$ is sparse then the number $2\text{nnz}(B)m$ flops. In cases they are both spares, the required flops will be no more than the minimum of these two quantities |
|transposition|$A^T$|$0$|Computing $A^T$ needs only copying, but no flops|
|Convolution|$a * b = T(a)b = T(b)a$|$2mn$||

One interesting discovery in the complexity of matrix product is that order matters. Different order of computing the same expression can result in different complexity. We first consider the vector product $ab^Tc$, where they are all $n$-th vectors. If we first evaluate $ab^T$, the cost is $n^2$ flops, and the cost of matrix-vector product $(ab^T)c$ is $2n^2$ flops. The total cost is $3n^2$ flops. If we first evaluate $b^Tc$ and then multiply by $a$, the total cost is $3n$ flops. Also, the first order requires storing an intermediate $n \times n$ matrix, while the latter only stores a scalar. 

Next, consider the product of three matrices 

$$
D = A_{m \times n}B_{n \times p}C_{p \times q}
$$
The first method is $(AB)C$. The complexity of $AB$ and $(AB)C$ are $2mnp$ and $2mpq$. for a total of $2mp(n + q)$ flops. 

The second method is $A(BC)$. We first compute product $BC$ ($2npq$ flops) and then form $D = A(BC)$, for a total of $2nq(m + p)$ flops. 

The two complexity are equal when 

$$
\frac{1}{n} + \frac{1}{q} = \frac{1}{m} + \frac{1}{p}
$$

When $m = p$ and $n = q$: 

$$
\begin{aligned}
\text{first method}&: \mathcal{O}(m^2n) \\
\text{second method}&: \mathcal{O}(mn^2)
\end{aligned}
$$

Therefore the complexity can vary dramatically according to the order of computing, when there is a great difference between $m$ and $n$.













