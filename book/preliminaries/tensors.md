$\newcommand{\beps}{\boldsymbol\varepsilon}$
$\newcommand{\bsig}{\boldsymbol\sigma}$
$\newcommand{\ud}{d}$
$\newcommand{\us}{\mathrm{s}}$
$\newcommand{\ba}{\mathbf{a}}$
$\newcommand{\bb}{\mathbf{b}}$
$\newcommand{\bc}{\mathbf{c}}$
$\newcommand{\bt}{\mathbf{t}}$
$\newcommand{\bu}{\mathbf{u}}$
$\newcommand{\bw}{\mathbf{w}}$
$\newcommand{\bN}{\mathbf{N}}$
$\newcommand{\bB}{\mathbf{B}}$
$\newcommand{\bD}{\mathbf{D}}$
$\newcommand{\bK}{\mathbf{K}}$
$\newcommand{\pder}[2]{\frac{\partial #1}{\partial #2}}$
$\newcommand{\iD}{\boldsymbol{\mathcal{D}}}$
$\newcommand{\mbf}[1]{\mathbf{#1}}$
$\newcommand{\mrm}[1]{\mathrm{#1}}$
$\newcommand{\bs}[1]{\boldsymbol{#1}}$
$\newcommand{\T}{^\mathrm{T}}$
$\newcommand{\myVec}[1]{\left\{ \begin{matrix} #1 \end{matrix} \right\}}$
$\newcommand{\myMat}[1]{\left[ \begin{matrix} #1 \end{matrix} \right]}$
$\newcommand{cA}[1]{\textcolor[RGB]{1,113,136}{#1}}$
$\newcommand{cB}[1]{\textcolor[RGB]{195,49,47}{#1}}$
$\newcommand{cC}[1]{\textcolor[RGB]{0,102,162}{#1}}$
$\newcommand{cD}[1]{\textcolor[RGB]{0,183,211}{#1}}$
$\newcommand{cE}[1]{\textcolor[RGB]{0,163,144}{#1}}$
$\newcommand{cF}[1]{\textcolor[RGB]{97,164,180}{#1}}$
$\newcommand{cG}[1]{\textcolor[RGB]{130,215,198}{#1}}$
$\newcommand{cH}[1]{\textcolor[RGB]{153,210,140}{#1}}$
$\newcommand{cI}[1]{\textcolor[RGB]{235,114,70}{#1}}$
$\newcommand{cJ}[1]{\textcolor[RGB]{241,190,62}{#1}}$
$\newcommand{cK}[1]{\textcolor[RGB]{231,41,138}{#1}}$

# Tensor basics

In this page, we will briefly cover basic tensor concepts which will be used throughout the rest of the book. Give this page a quick look at first and keep referring back to it as you go through the rest of the content in case the notation is unclear to you.

We start with a brief comment on the different notation systems we will be using. Scalars are always represented by lower-case symbols, for instance:

$$
a, b, c, \phi
$$(p-t-scalars)

For vectors and matrices, apart from writing down all their components in full, we will be using the following three notation systems:

````{tab-set}
```{tab-item} Matrix/vector notation
Vectors represented by lower-case **bold** characters:

$$
\ba, \bb, \bc, \bs{\phi}
$$

Matrices represented by upper-case **bold** characters:

$$
\bN, \bB
$$

Higher-order tensors cannot be represented.

$$
\phantom{a}
$$

Vector operations made unique by transposing them:

$$
\mbf{A} = \bb\bc\T
\quad
a = \bb\T\bc
$$

```
```{tab-item} Tensor notation
Vectors represented by lower-case **bold** characters:

$$
\ba, \bb, \bc, \bs{\phi}
$$

Matrices represented by upper-case **bold** characters:

$$
\bN, \bB
$$

Higher-order tensors represented by **bold** calligraphic characters:

$$
\bs{\mathcal{C}}, \bs{\mathcal{D}}
$$

Vector operations made unique through different symbols:

$$
\mbf{A} = \bb\otimes\bc
\quad
a = \bb\cdot\bc
$$

```
```{tab-item} Index notation
Vectors represented by a single subscript:

$$
a_i, b_j
$$

Matrices represented by two subscripts:

$$
N_{ij}, B_{ij}
$$

Higher-order tensors represented by more subscripts:

$$
C_{ijk}, D_{ijkl}
$$

Operations made unique by summing over repeated symbols:

$$
A_{ij} = b_ic_j
\quad
a = b_ic_i
$$

where the repeated index $i$ in $a=b_ic_i$ implies that summation takes place $b_ic_i\equiv\sum_ib_ic_i$. 
```
````

As scalars require no further explanation, we can move straight to vectors.

## Vectors 

First-order tensors are also known as vectors. In space $\mathbb{R}^m$, they may be expressed in terms of their components. For instance in a 3D space ($m=3$):

$$
\ba = a_i = \myMat{a_1\\a_2\\a_3}
$$(p-t-vectordef)

where in index notation it is usual to adopt indices $i$, $j$, $k$ and $l$ ranging between $1$ and the number of dimensions of the PDE we are solving (i.e. $n=2$ for 2D problems and $n=3$ for 3D problems).

We often need to compute the $L_2$ norm of vectors, given by:

$$
\lVert\ba\rVert = \sqrt{\ba\T\ba} = \sqrt{\ba\cdot\ba} = \sqrt{a_ia_i}
$$(p-t-l2vecnorm)

which is therefore the square root of the sum of the squared vector components. When using index notation, remember that summation (in this case over $i$) is implied.

## Matrices

Second-order tensors are also known as matrices. A matrix in space $\mathbb{R}^{m\times n}$ may be expressed in terms of its components. For instance with $m=n=3$ we have:

$$
\mbf{A} = a_{ij} = \myMat{A_{11} & A_{12} & A_{13}\\A_{21} & A_{22} & A_{23}\\A_{31} & A_{32} & A_{33}}
$$(p-t-matrixdef)

A matrix is said to be **square** when it has as many rows as columns ($m=n$). A square matrix is said to be **diagonal** when only its diagonal entries are non-zero:

$$
\mbf{A} = \myMat{A_{11} & 0 & 0\\0 & A_{22} & 0\\ 0 & 0 & A_{33}}
$$(p-t-diagmatrix)

and one important diagonal matrix is the **identity matrix**:

$$
\mbf{I} = \myMat{1&0&0\\0&1&0\\0&0&1}
$$(p-t-idmatrix)
whose entries can be represented in index notation by the **Kronecker delta** function:

$$
\delta_{ij} =
\begin{cases}
0 & \text{if } i\neq j\\
1 & \text{if } i=j
\end{cases}
$$(p-t-kronecker)

A matrix is said to be **symmetric** when its off-diagonal entries are mirrored with respect to the diagonal:

$$
\mbf{A} = \myMat{a&\cA{b}&\cB{c}\\\cA{b}&d&\cI{e}\\\cB{c}&\cI{e}&f}
$$(p-t-symmatrix)

By interchanging rows and columns we can get the **transpose** of a matrix:

$$
\mbf{A} = \myMat{\cA{a}&\cA{b}&\cA{c}\\\cB{d}&\cB{e}&\cB{f}\\\cI{g}&\cI{h}&\cI{i}}
\quad
\mbf{A}\T = \myMat{\cA{a}&\cB{d}&\cI{g}\\\cA{b}&\cB{e}&\cI{h}\\\cA{c}&\cB{f}&\cI{i}}
$$(p-t-transpose)  

which also implies that for a symmetric matrix $\mbf{A}$ we can write $\mbf{A}\T=\mbf{A}$. For a symmetric matrix we can also write in index notation:

$$
A_{ij} = A_{ij}\T = A_{ji}\Longleftrightarrow\mbf{A}\text{ is symmetric}
$$(p-t-symmatrixidx)

Finally, a matrix is said to be **sparse** if most of its entries are zero. For instance, diagonal matrices are intrinsically sparse, as are several important matrices involved in the Finite Element Method. The opposite of a sparse matrix is a **dense** matrix. 

