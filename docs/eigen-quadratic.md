
# Eigenthings and quadratic forms


## Eigenvectors and eigenvalues  

\BeginKnitrBlock{definition}\iffalse{-91-69-105-103-101-110-118-101-99-116-111-114-115-32-97-110-100-32-101-105-103-101-110-118-97-108-117-101-115-93-}\fi{}<div class="definition"><span class="definition" id="def:eigen"><strong>(\#def:eigen)  \iffalse (Eigenvectors and eigenvalues) \fi{} </strong></span>An **eigenvector** of an $n \times n$ matrix $A$ is a *nonzero* vector $\boldsymbol{x}$ such that $A\boldsymbol{x} = \lambda\boldsymbol{x}$. 

$\lambda$ is the **eigenvalue** of $A$ if there is a nontrivial solution $\boldsymbol{x}$ of $A\boldsymbol{x} = \lambda \boldsymbol{x}$; such an $\boldsymbol{x}$ is called an *eigenvector corresponding to $\lambda$*</div>\EndKnitrBlock{definition}

To find eigenvalues and corresponding eigenvectors of $A$, we look at the equation 

$$
(A - \lambda I)\boldsymbol{x}= 0
$$

Since eigenvector $\boldsymbol{x}$ must be nonzero, $(A - \lambda I)$ is a singular matrix 


\begin{equation}
(\#eq:characteristic-equation)
\det (A - \lambda I) = 0
\end{equation}

Eq \@ref(eq:characteristic-equation) is called the **characteristic equation** of matrix $A$. This is a scalar equation containing information about eigenvalues and eigenvectors of a square matrix $A$. 



\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-1"><strong>(\#thm:unnamed-chunk-1) </strong></span>Eigenvalues of a trangular matrix are its diagonal entries.</div>\EndKnitrBlock{theorem}


**PROOF**  

Consider the $3 \times 3$ case. If $A$ is upper triangular, then $A - \lambda I$ has the form 

$$
\begin{bmatrix}
a_{11} - \lambda & a_{12} & a_{13} \\
0 & a_{22} - \lambda & a_{23}  \\
0 & 0 & a_{33} - \lambda
\end{bmatrix}
$$
So the roots of characteristic are $a_{11}, a_{22}, a_{33}$ respectively. 

There are some useful results about how eigenvalues change after various manipulations. 

1. For any $k, b \in \mathbb{R}$, $\boldsymbol{x}$ is an eigenvector of $kA + bI$ with eigenvalue $k\lambda + b$  

**PROOF**
$$
(kA + bI)\boldsymbol{x} = kA\boldsymbol{x} + bI\boldsymbol{x} = k \lambda\boldsymbol{x} + b\boldsymbol{x} = (k\lambda + b)\boldsymbol{x} 
$$


2, If $A$ is invertible, then $\boldsymbol{x}$ is an eigenvector of $A^{-1}$ with eigenvalue $1/\lambda$  

**PROOF**

$$
\boldsymbol{x} = A^{-1}A\boldsymbol{x} =  A^{-1}\lambda \boldsymbol{x} = \lambda A^{-1}\boldsymbol{x}
$$
3. $A^{k}\boldsymbol{x} = \lambda^{k}\boldsymbol{x}$ 


The next theorem is important in terms of diagonalization and spectral decomposition

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:distinct-eigenvalue"><strong>(\#thm:distinct-eigenvalue) </strong></span>For distinct eigenvalues $\lambda_1, \cdots, \lambda_r$ of an $n \times n$ matrix A, their corresponding eigenvectors $\boldsymbol{v_1}, ..., \boldsymbol{v_r}$ are linearly independent. </div>\EndKnitrBlock{theorem}

**PROOF**  

Suppose for r distinct eigenvalue  $\lambda_1, \cdots, \lambda_r$, the set $\{\boldsymbol{v_1}, ..., \boldsymbol{v_r}\}$ is not linearly independent, and $p$ is the least index such that $\boldsymbol{v}_{p+1}$ is a linear combination of the preceding vectors. Then there exists scalars $c_1, \cdots, c_p$ such that

$$
c_1\boldsymbol{v}_1 + \cdots + c_p\boldsymbol{v}_p = \boldsymbol{v}_{p+1} \tag{1}
$$
Left multiply by $A$, and note we have $A\boldsymbol{v}_i = \lambda_i\boldsymbol{v}_i$ for $i = 1, ..., n$ 

$$
c_1\lambda_1\boldsymbol{v}_1 + \cdots + c_p\lambda_p\boldsymbol{v}_p = \lambda_{p+1}\boldsymbol{v}_{p+1} \tag{2}
$$
Multiplying both sides of (2) by $\lambda_{p+1}$ and subtracting (2) from the result 

$$
c_1(\lambda_1 - \lambda_{p+1})\boldsymbol{v}_1 +\cdots + c_p(\lambda_p - \lambda_{p+1})\boldsymbol{v}_p = 0 \tag{3}
$$
Since $\boldsymbol{v}_1, ..., \boldsymbol{v}_p$ are linearly independent,  weights in (3) must be all zero. Since $\lambda_1, \cdots, \lambda_p$ are distinct, hence $c_i = 0, \, i = 1, ..., p$. But then (5) says that eigenvector $\boldsymbol{v}_{p+1}$ is zero vector, which contradicts definition \@ref(def:eigen) 

## Diagnolization and similar matrices 


\BeginKnitrBlock{definition}\iffalse{-91-68-105-97-103-111-110-97-108-105-122-97-116-105-111-110-32-116-104-111-101-114-101-109-93-}\fi{}<div class="definition"><span class="definition" id="def:diagonalization"><strong>(\#def:diagonalization)  \iffalse (Diagonalization thoerem) \fi{} </strong></span>An $n \ times n$ matrix $A$ is diagnolizable **if and only if** A has $n$ independent linearly independent eigenvectors. 

In such case, in $A = P \Lambda P^{-1}$, the diagonal entries of $D$ are eigenvalues that correpond, respectively, to the eigenvectors of in $P$  
  
In other words, $A$ is diagnolizable if and only if there are enough eigenvectors in form a basis of $R^n$, called an **eigenvector basis** of $R^n$ </div>\EndKnitrBlock{definition}

**Proof** 

$$
\begin{split}
AP &= A[\boldsymbol{v}_1 \cdots \boldsymbol{v}_n] \\
   &= [A\boldsymbol{v}_1 \cdots A\boldsymbol{v}_n] \\ 
   &= [\lambda_1\boldsymbol{v}_1 \cdots \lambda_n\boldsymbol{v}_n]
\end{split}
$$
while on the other side of the equation:  

$$
\begin{aligned}
DP &= 
[\boldsymbol{v}_1 \cdots \boldsymbol{v}_n]
\begin{bmatrix}
\lambda_1 & 0 & \cdots & 0\\
0  & \lambda_2 & \cdots & 0 \\
\vdots & \vdots & & \vdots \\
0 & 0 & \cdots & \lambda_n 
\end{bmatrix} 
 \\
&= [\lambda_1\boldsymbol{v}_1 \cdots \lambda_n\boldsymbol{v}_n]
\end{aligned}
$$

So that 

$$
\begin{aligned}
AP &= PD \\
A &= P \Lambda P^{-1}
\end{aligned}
$$
Because $P$ contains $n$ independent columns so it's invertible.  

According to theorem \@ref(thm:distinct-eigenvalue), an $n \times n$ matrix with $n$ distinct eigenvalues is diagonalizable. This is a sufficient condition. 

For matrices whose eigenvalues are not distinct, there is still a change that it is diagonalizable. For any matrix $A_{n\times n}$, as long as the sum of the dimensions of the eigenspaces equals $n$ then $P$ is invertible. This could happen in the following two scenarios

1. The characteristic polynomial factors completely into linear factors. This is the case when $A$ has n distinct eigenvalues. 

2. The dimension of the eigenspace for each $\lambda_k$ equals the multiplicity of $\lambda_k$. Thus $A$ with repeated eigenvalues can still be diagonalizable. 

### similarity

If $A$ and $B$ are both $n \times n$ matrices, then $A$ **is similar to** $N$ if there is an invertible matrix $P$ such that $P^{-1}AP = B$, or equivalently if we write $Q$ for $P^{-1}$, $Q^{-1}BQ = A$. Changing $A$ into $P^{-1}AP$ is called a **similarity transformation**.  




\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-2"><strong>(\#thm:unnamed-chunk-2) </strong></span>If $A$ and $B$ are similar, they have the same eigenvalues. </div>\EndKnitrBlock{theorem}

**PROOF**  
If $B = P^{-1}AP$, then 

$$
B - \lambda I = P^{-1}AP - \lambda P^{-1}P = P^{-1}(AP - \lambda P) =  P^{-1}(A - \lambda I) P
$$
so that 

$$
\det (B - \lambda I ) = \det(P) \cdot \det(A - \lambda I ) \cdot \det(P^{-1})
$$
since $\det(P) \cdot \det(P^{-1}) = \det (I) = 1$, we have 

$$
\det (B - \lambda I)  = \det(A - \lambda I)
$$

As a result of their identical characteristic polynomial, $B$ and $A$ have the same eigenvalues. We can also show that eigenvector of $B$ is $P\boldsymbol{v}$:

$$
\begin{aligned}
A\boldsymbol{v} &= \lambda\boldsymbol{v} \\
(P^{-1}BP)\boldsymbol{v} &= \lambda\boldsymbol{v} \\
P(P^{-1}BP)\boldsymbol{v} &= \lambda P\boldsymbol{v} \\
B(P\boldsymbol{v}) = \lambda P \boldsymbol{v}
\end{aligned}
$$



The similarity theorem leads to a interesting proposition. 

\BeginKnitrBlock{proposition}<div class="proposition"><span class="proposition" id="prp:unnamed-chunk-3"><strong>(\#prp:unnamed-chunk-3) </strong></span>For $A, B \in \mathbb{R}^{n \times n}$, $AB$ and $BA$ are similar matrices and therefore share the same set of eigenvalues.  </div>\EndKnitrBlock{proposition}

To prove this, we need to show that there exists a invertible matrix $A$ such that $P^{-1}(AB)P = BA$. Take $P = A$ and the equation holds.  

It is easy to show that similarity is **transitive**: if $A$ is similar to $B$, $B$ is similar to $C$, then $A$ is similar to $C$. So similarity means a family of matrices with the same set of eigenvalues, the most special and simplest of which is the diagonal matrix (if this is an diagonalizable family). Some computer algorithms calculate eigenvalues of $A$ in this manner: with a sequential choices of $P$, the off-diagonal elements of $A$ become smaller and smaller until $A$ becomes a triangular matrix or diagonal matrix, whose eigenvalues are simply diagonal entries and is the same as $A$.


It is obvious that a diagonalizable matrix $A$ is similar to diagonal matrix $D$, whose diagonal entries are $A$'s eigenvalues $\lambda_i$, and $P = [\boldsymbol{v}_1 \;\; \cdots \;\; \boldsymbol{v}_n]^{-1}$ where $\boldsymbol{v}_i, \;i = 1,..., n$ are eigenvectors corresponding to $\lambda_i$. 

But square matrix $A$ can still be similar to matrices other than $D$ with other choices of $P$, and non-diagonal matrices can also have similar matrices of their own. In fact, **every square matrix is similar to a matrix in Jordan matrix** \@ref(jordan-matrix). 


<hr>

Similarity is only a *sufficient* condition for identical eigenvalues. The matrices 

$$
\begin{bmatrix}
2 & 1 \\
0 & 2 
\end{bmatrix}
\;\text{and}\;
\begin{bmatrix}
2 & 0 \\
0 & 2 
\end{bmatrix}
$$
are not similar even though they have the same eigenvalues. 


### Jordan matrix

For non-diagonalizable matrices $A_{n \times n}$, the goal is to with similar transformation $P^{-1}AP$ construct a matrix that is as nearest to a diagonal matrix as possible.  


\BeginKnitrBlock{definition}<div class="definition"><span class="definition" id="def:unnamed-chunk-4"><strong>(\#def:unnamed-chunk-4) </strong></span>The $n \times n$ matrix $J_{\lambda, n}$ with $\lambda$s on the diagonal, $1$s on the superdiagonal and $0$s elsewhere is called a Jordan matrix. A Jordan matrix in Jordan normal form is a block matrix that has Jordan blocks down its block diagonal and is zero elsewhere</div>\EndKnitrBlock{definition}

An example of Jordan matrix, the appearance of $\lambda_i$ on the diagonal is equal to its multiplicity as $A$'s eigenvalue. 
$$
\begin{bmatrix}
\lambda_1 & 1  & \\
& \lambda_1 & 1 & \\
& & \lambda_1 & \\ 
& & & \lambda_2 & 1 \\
& & & & \lambda_2  \\ 
& & & & & \lambda_3 & 1  \\ 
& & & & & & \ddots \\
& & & & & & & \lambda_n & 1 \\
& & & & & & & & \lambda_n
\end{bmatrix}
$$
An illustration from [wikipedia](https://en.wikipedia.org/wiki/Jordan_normal_form), the circled area is the Jordan blcok. 
<img src="images/jordan-blocks.png" width="40%" style="display: block; margin: auto;" />

Though the purpose of this section was not the computation details of Jordan matrices, it helps to give a concrete example. Consider $A$

$$
A = 
\begin{bmatrix}
5 & 4 & 2 & 1 \\
0 & 1 & -1 & -1 \\
-1 & -1 & 3 & 0 \\
1 & 1 & -1 & 2
\end{bmatrix}
$$

Including multiplicity, the eigenvalues of $A$ are $\lambda = 1, 2, 4, 4$. And for $\lambda = 4$, the eigenspace is 1 dimensional instead of 2, meaning $A$ is not diagonalizable. Nonetheless, $A$ is similar to the following Jordan matrix 

$$
J = 
\begin{bmatrix}
1 & 0 & 0 & 0\\
0 & 2 & 0 & 0\\
0 & 0 & 4 & 1\\
0 & 0 & 0 & 4
\end{bmatrix}
$$

To obtain $P$, recall that $P^{-1}AP = J$. Let $P$ have column vectors $p_i, \; i = 1,...,4$, then:

$$
A[\boldsymbol{p}_1 \; \; \boldsymbol{p}_2 \;\; \boldsymbol{p}_3 \;\; \boldsymbol{p}_4] = [\boldsymbol{p}_1 \; \; \boldsymbol{p}_2 \;\; \boldsymbol{p}_3 \;\; \boldsymbol{p}_4]
\begin{bmatrix}
1 & 0 & 0 & 0\\
0 & 2 & 0 & 0\\
0 & 0 & 4 & 1\\
0 & 0 & 0 & 4
\end{bmatrix}
= [\boldsymbol{p}_1 \;\; 2\boldsymbol{p}_2 \;\; 4\boldsymbol{p}_3 \;\; \boldsymbol{p}_3 + 4\boldsymbol{p}_4]
$$

We see that 

$$
\begin{aligned}
(A - 1I)\boldsymbol{p}_1 &= \boldsymbol{0} \\
(A - 2I)\boldsymbol{p}_2 &= \boldsymbol{0} \\
(A - 4I)\boldsymbol{p}_3 &= \boldsymbol{0} \\
(A - 1I)\boldsymbol{p}_4 &= \boldsymbol{p}_3 
\end{aligned}
$$
The solutions $\boldsymbol{p}_i$ are called **generalized eigenvectors** of $A$. 

## Symmetric matrices 

A *square* matrix $A \in \mathbb{R}^{n \times n}$ is *symmetric* if $A = A^{T}$, and *anti-symmetric* if $A = - A^{T}$. 

It can be shown that for any $A \in \mathbb{R}^{n \times n}$, $A + A^T$ is symmetric and $A - A^T$ anti-symmetric. So any square matrix $A$ can be wrote as a sum of a symmetric matrix and an anti-symmetric matrix 

$$
A = \frac{1}{2}(A + A^T) + \frac{1}{2}(A - A^T)
$$

It is common to denote the set of all symmetric matrices of size $n$ as $\mathbb{S}^n$, and $A \in \mathbb{S}^n$ means $A$ is a symmetric $n \times n$ matrix. 


Symmetric matrices have some nice properties about diagonalization.  

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-6"><strong>(\#thm:unnamed-chunk-6) </strong></span>If $A$ is symmetric, eigenvectors from distinct eigenvalues are **orthogonal**. </div>\EndKnitrBlock{theorem}

**PROOF** 

Let $\boldsymbol{v}_1$ and $\boldsymbol{v}_2$ be eigenvectors that correspond to distinct eigenvalues $\lambda_1$ and $\lambda_2$. Compute 

$$
\begin{split}
\lambda_1\boldsymbol{v}_1 \cdot \boldsymbol{v}_2 &= (\lambda_1\boldsymbol{v}_1)^T\boldsymbol{v}_2 \\
&= (\boldsymbol{v}_1^TA^T)\boldsymbol{v}_2 \\
&= \boldsymbol{v}_1^T(A\boldsymbol{v}_2) \\
&= \boldsymbol{v}_1^T(\lambda_2\boldsymbol{v}_2) \\
&= \lambda_2\boldsymbol{v}_1 \cdot \boldsymbol{v}_2
\end{split}
$$
because $\lambda_1 \not = \lambda_2$, $\boldsymbol{v}_1 \cdot \boldsymbol{v}_2 = 0$.

For symmetric matrices $A \in \mathbb{R}^{n \times n}$ without $n$ distinct eigenvalues, it turns out that the dimension of the eigenspace for each $\lambda_k$ always equals the multiplicity of $\lambda_k$. For this reason, if $A$ is a symmetric matrix we can always construct a orthonormal set $\{\boldsymbol{q}_1 \;\; \cdots \;\; \boldsymbol{q}_n\}$ from $\{\boldsymbol{v}_1 \;\; \cdots \;\; \boldsymbol{v}_n\}$ such that  

$$
P^{T} = 
\begin{bmatrix}
\boldsymbol{q}_1^T \\
\vdots \\ 
\boldsymbol{q}_n^T
\end{bmatrix}
= P^{-1}
$$
Recall that matrix $A$ with $n$ linearly independent eigenvectors is diagonalizable and can be written as 

$$
A = P \Lambda P^{-1}
$$
where $P = [\boldsymbol{v}_1 \;\; \cdots \;\; \boldsymbol{v}_n]$ and $D$ is a diagonal matrix with eigenvalues on its diagonal entries. 

With symmetric matrices, after proper transformation we have $P^T = P^{-1}$, so that 

\begin{equation}
(\#eq:orthogonal-diagonalization)
A = Q \Lambda Q^{T}
\end{equation}

Such matrix $A$ is said to be **orthogonally diagonalizable**. 

We have seen that for symmetric matrix $A$, Eq \@ref(eq:orthogonal-diagonalization) always holds. We can also also verify that if $A$ is orthogonally diagonalizable then it is a symmetric matrix

$$
A^T = (Q \Lambda Q^{T})^T = PD^TP^T = Q \Lambda Q^{T}  = A
$$

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-7"><strong>(\#thm:unnamed-chunk-7) </strong></span>An $n \times n$ matrix $A$ is orthogonally diagonalizable if an only if $A$ is a symmetric matrix. </div>\EndKnitrBlock{theorem}

### Spectral decomposition 

For orthogonally diagonalizable matrix $A$, we have 

$$
A = Q \Lambda Q^{T} = [\boldsymbol{q}_1 \;\; \cdots \;\; \boldsymbol{q}_n] 
\begin{bmatrix}
\lambda_1 & & \\
 & \ddots \\
 & & \lambda_n
\end{bmatrix}
\begin{bmatrix}
\boldsymbol{q}_1^T \\
\vdots \\
\boldsymbol{q}_n
\end{bmatrix}
$$

It follows that 

\begin{equation}
(\#eq:spectral-decomposition)
A = \lambda_1\boldsymbol{q}_1\boldsymbol{q}_1^T + \cdots + \lambda_1\boldsymbol{q}_n\boldsymbol{q}_n^T
\end{equation}

Eq \@ref(eq:spectral-decomposition) is called the **spectral decomposition**, breaking $A$ into pieces of rank 1 matrix. It got this name because he set of eigenvalues of a matrix $A$ is sometimes called its *spectrum*.  




## Quadratic forms 

\BeginKnitrBlock{definition}\iffalse{-91-81-117-97-100-114-97-116-105-99-32-102-111-114-109-93-}\fi{}<div class="definition"><span class="definition" id="def:unnamed-chunk-8"><strong>(\#def:unnamed-chunk-8)  \iffalse (Quadratic form) \fi{} </strong></span>A **quadratic form** on $\mathbb{R}^n$ is a function $Q$ defined on $\mathbb{R}^n$ whose value at a vector $\boldsymbol{x}$ in $\mathbb{R}^n$ can be computed by an expression of the form $Q(\boldsymbol{x}) = \boldsymbol{x}^TA\boldsymbol{x}$, where $A \in \mathbb{R}^{n \times n}$ is a **symmetric** matrix. $A$ is called the matrix of the quadraticc form. </div>\EndKnitrBlock{definition}

There exists a one-to-one mapping between symmetric matrix $A$ and the quadratic form. Consider the $3 \times 3$ case: 

$$
\boldsymbol{x} =
\begin{bmatrix}
x_1 \\
x_3 \\
x_3 \\
\end{bmatrix}
, \;\; A = 
\begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33} 
\end{bmatrix} \\
$$

$$
\begin{split}
\boldsymbol{x}^TA\boldsymbol{x} &= 
[x_1 \;\; x_2 \;\; x_3]
\begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33} 
\end{bmatrix}
\begin{bmatrix}
x_1 \\
x_3 \\
x_3 \\
\end{bmatrix} \\
&= a_{11}x_1^2 + a_{22}x_2^2 + a_{33}x_3^2 + \\
& \quad(a_{12} + a_{21})x_1x_2 + (a_{13} + a_{31})x_1x_3 + (a_{23} + a_{32})x_2x_3 
\end{split} 
\tag{1}
$$
Since $A$ is symmetric, we have $a_{ij} = a_{ji}$, thus 

$$
\boldsymbol{x}^TA\boldsymbol{x}  = a_{11}x_1^2 + a_{22}x_2^2 + a_{33}x_3^2 + 2a_{12}x_1x_2 + 2a_{13}x_1x_3 + 2a_{23}x_2x_3 \tag{2} 
$$
This verifies that $\boldsymbol{x}^TA\boldsymbol{x}$ when $A \in \mathbb{R}^{n \times n}$ is symmetric does result in a quadratic function of $n$ variables. Conversely, any quadratic function of $n$ variables, like shown in $(2)$, can be expressed in terms of $\boldsymbol{x}^TA\boldsymbol{x}$ with unique choice of symmetric matrix $A \in \mathbb{R}^{n \times n}$.  

### Change of variabele 

If $\boldsymbol{x}$ is a variable vector in $\mathbb{R}^n$, then a *change of variable* is an equation of the form 

$$
\begin{aligned}
\boldsymbol{x} &= P\boldsymbol{y} \\
\text{or equivalently} \quad \boldsymbol{y} &= P^{-1}\boldsymbol{x}
\end{aligned}
$$
\BeginKnitrBlock{theorem}\iffalse{-91-84-104-101-32-80-114-105-110-99-105-112-97-108-32-65-120-101-115-32-84-104-101-111-114-101-109-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-9"><strong>(\#thm:unnamed-chunk-9)  \iffalse (The Principal Axes Theorem) \fi{} </strong></span>Let $A$ be an $n \times n$ symmetric matrix. Then there is an orthogonal change of variable, $\boldsymbol{x} = P\boldsymbol{y}$, this transform the quadratic form $\boldsymbol{x}^TA\boldsymbol{x}$ into a quadratic form $\boldsymbol{y}^TD\boldsymbol{y}$ with no cross-product term.  

$P$ is constructed with $A$'s orthonormal eigenvectors $\boldsymbol{q}_1, ..., \boldsymbol{q}_n$. According to theorem \@ref(eq:orthogonal-diagonalization): 

$$
\boldsymbol{x}^TA\boldsymbol{x} = (P\boldsymbol{y})^TA(P\boldsymbol{y}) = \boldsymbol{y}^TP^{T}AP\boldsymbol{y} = \boldsymbol{y}^TD\boldsymbol{y}
$$</div>\EndKnitrBlock{theorem}

The principle axes theorem \@ref(thm:the-principal-axes-theorem) shows that if $A$ is diagonalizable, quadratic form $\boldsymbol{x}^TA\boldsymbol{x}$ can be reexpressed into the form $\lambda_1y_1^2 + \lambda_2y_2^2 +  \cdots + \lambda_ny_n^2$ with change of variables $\boldsymbol{x} = P\boldsymbol{y}$. 

### Classification of quadratic forms 

- A symmetric matrix $A \in \mathbb{S}^n$ is **positive definite** (PD) if for all non-zero vectors $\boldsymbol{x} \in \mathbb{R}^n,\; \boldsymbol{x}^TA\boldsymbol{x} > 0$. We can denote positive definite matrix $A$ as $A \succ 0$ (or $A > 0$). The set of all positive definite matrices is denoted as $\mathbb{S}_{++}^n$  

- A symmetric matrix $A \in \mathbb{S}^n$ is **positive semidefinite** (PSD) if for all non-zero vectors $\boldsymbol{x} \in \mathbb{R}^n,\; \boldsymbol{x}^TA\boldsymbol{x} \ge 0$. We can denote positive definite matrix $A$ as $A \succeq 0$ (or $A \ge 0$). The set of all positive semidefinite matrices is denoted as $\mathbb{S}_{+}^n$  

- A symmetric matrix $A \in \mathbb{S}^n$ is **negative definite** (ND), denoted by $A \prec 0$ (or $A < 0$),  if for all non-zero vectors $\boldsymbol{x} \in \mathbb{R}^n,\; \boldsymbol{x}^TA\boldsymbol{x} < 0$.  

- Similarly, a symmetric matrix $A \in \mathbb{S}^n$ is **negative semidefinite** (NSD), denoted by $A \preceq 0$ (or $A \le 0$),  if for all non-zero vectors $\boldsymbol{x} \in \mathbb{R}^n,\; \boldsymbol{x}^TA\boldsymbol{x} \le 0$.   

- Finally,  a symmetric matrix $A \in \mathbb{S}^n$ is **indefinite**, if it is neither positive semidefinite or negative semidefinite. In other words, if there exists $\boldsymbol{x}, \boldsymbol{x}', \in \mathbb{R}^{n}$ such taht $\boldsymbol{x}^TA\boldsymbol{x} > 0$ and $\boldsymbol{x'}^TA\boldsymbol{x}' > 0$

\BeginKnitrBlock{rmdnote}<div class="rmdnote">Note that when talking about $A$ being PD, PSD, ND, NSD or indefinite, $A$ is always assumed to be **symmetric**.

Also, if $A$ is positive definite, then $−A$ is negative definite and viceversa. Likewise, if $A$ is positive semidefinite then $−A$ is negative semidefinite and vice versa. If $A$ is indefinite, then so is $−A$. </div>\EndKnitrBlock{rmdnote}

From theorem \@ref(thm:the-principal-axes-theorem), we know that the sign of eigenvalues are closely related to classifications of symmetric matrices here. Take positive definite matrices for example, the following statements of $A$ are equivalent: 

- For any $\boldsymbol{x} \in \mathbb{R}^n, \; \boldsymbol{x}^TA\boldsymbol{x} > 0$  

- Let $\lambda_i, \; i = 1, ..., n$ be $A$'s eigenvalues, $\lambda_i > 0$  

- All leading determinants of $A > 0$  

- All pivots are $> 0$  


Classification of $A \in \mathbb{S}^{n}$ by its eigenvalue can be applied in general. 

\BeginKnitrBlock{theorem}\iffalse{-91-81-117-97-100-114-97-116-105-99-32-102-111-114-109-115-32-97-110-100-32-101-105-103-101-110-118-97-108-117-101-115-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:unnamed-chunk-11"><strong>(\#thm:unnamed-chunk-11)  \iffalse (Quadratic forms and eigenvalues) \fi{} </strong></span>Let $$A \in \mathbb{S}^{n}$$. Then the quadratic form $\boldsymbol{x}^TA\boldsymbol{x}$ and $A$ is: 
   
- positive definite if and only if the eigenvalues of $A$ are all positive  

- negative definite if and only if the eigenvalues of $A$ are all negative  

- indefinite if and only if $A$ has both positive and negative eigenvalues</div>\EndKnitrBlock{theorem}

## Rayleigh quotients 

Let $A \in \mathbb{S}^n$ and $\boldsymbol{x} \in \mathbb{R}^n$, **Rayleigh quotient** is defined as 

$$
R_{A}(\boldsymbol{x}) = \frac{\boldsymbol{x}^TA\boldsymbol{x}}{\boldsymbol{x}^T\boldsymbol{x}}
$$
The Rayleigh quotient has some nice properties: 

- scale invariance: for any vector $\boldsymbol{x} \not= 0$ and any scalar $\alpha \not= 0$, $R_{A}(\boldsymbol{x}) = R_{A}(\alpha\boldsymbol{x})$  

- If $\boldsymbol{x}$ is a eigenvector of $A$ with eigenvalue $\lambda$, then $R_{A}(\boldsymbol{x}) = \lambda$

- The Rayleigh quotient is bounded by the largest and smallest eigenvalue of $A$, i.e. 

$$
\lambda_{\text{min}}(A) \le R_{A}(\boldsymbol{x}) \le \lambda_{\text{max}}(A)
$$

**PROOF** 

Since the Rayleigh quotient does not depend on the 2-norm of vector $\boldsymbol{x}$, we may assume a unit vector $\boldsymbol{x}^T\boldsymbol{x} = 1$. 

Next, orthogonally diagonalize $A$ as $Q \Lambda Q$

## SVD  

$$
\begin{split}
U\Sigma &= [\boldsymbol{q}_1 \;\; \cdots \;\; \boldsymbol{q}_n]
\begin{bmatrix}
\sigma_1 \\
& \ddots &  \\ 
& & \sigma_r \\
& & & 0 \\
& & & & \ddots \\
& & & & & 0 \\
\end{bmatrix} \\
&= [\sigma_1\boldsymbol{q}_1 \;\; \cdots \;\; \sigma_n\boldsymbol{q}_n] \\
& = [A\boldsymbol{v}_1 \;\; \cdots \;\; A\boldsymbol{v}_n] \\
&= AV
\end{split}
$$
