$\newcommand{\beps}{\boldsymbol\varepsilon}$
$\newcommand{\bsig}{\boldsymbol\sigma}$
$\newcommand{\ud}{\mathrm{d}}$
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
$\newcommand{\inv}{^{-1}}$
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

# Tensor calculus

In this page we go through a few basic vector calculus results that will be used throughout the rest of the book. We build upon the {ref}`notations<tensors>` and {ref}`linear algebra<linear_algebra>` concepts from the previous pages.

## Derivatives, gradients, divergence

In FEM we will often deal with spatial derivatives. We will be representing partial derivatives in two different notations. Let $u(\mbf{x})$ be a function dependent on spatial coordinates $\mbf{x}$. Some partial spatial derivatives of this function could be:

$$
\displaystyle\frac{\partial u}{\partial x} = u_{,x}
\quad
\displaystyle\frac{\partial u}{\partial y} = u_{,y}
\quad
\frac{\partial^2u}{\partial x^2} = u_{,xx}
\quad
\frac{\partial^2u}{\partial x\partial y} = u_{,xy}
$$(p-c-derivatives)

We can gather the first order derivatives into a **gradient vector**, which we represent by using the operator $\nabla$. Assuming $\mbf{x}$ is three-dimensional, we have:

$$
\nabla u = \myMat{\displaystyle\frac{\partial u}{\partial x}\\\displaystyle\frac{\partial u}{\partial y}\\\displaystyle\frac{\partial u}{\partial z}}
$$(p-c-gradu)

which we can also neatly represent using index notation:

$$
\nabla u = \displaystyle\frac{\partial u}{\partial x_i} = u_{,i}
$$(p-c-graduindex)

Note above how the operator $\nabla$ increases the dimensionality of its operand by one. We can generalize this result by taking the gradient of a vector, which results in a matrix:

$$
\nabla\mbf{a} = \displaystyle\frac{\partial a_i}{\partial x_j} = a_{i,j} = 
\myMat{
\displaystyle\frac{\partial a_x}{\partial x} & \displaystyle\frac{\partial a_x}{\partial y} & \displaystyle\frac{\partial a_x}{\partial z}\\
\displaystyle\frac{\partial a_y}{\partial x} & \displaystyle\frac{\partial a_y}{\partial y} & \displaystyle\frac{\partial a_y}{\partial z}\\
\displaystyle\frac{\partial a_z}{\partial x} & \displaystyle\frac{\partial a_z}{\partial y} & \displaystyle\frac{\partial a_z}{\partial z}\\
}
$$(p-c-gradvec)

We can also define the **divergence** operator using the same symbol $\nabla$ but one that takes the opposite role of aggregating derivatives in all directions and reducing the dimensionality of its operand by one. For a vector this would be defined as:

$$
\nabla\cdot\mbf{a} = \displaystyle\frac{\partial a_i}{\partial x_i} = a_{i,i} = \displaystyle\frac{\partial a_x}{\partial x} + \frac{\partial a_y}{\partial y} + \frac{\partial a_z}{\partial z}
$$(p-c-divvec)

resulting in a scalar. We can define an analogous operation for a matrix, which then results in a vector:

$$
\nabla\cdot\mbf{A} = \displaystyle\frac{\partial A_{ij}}{\partial x_j} = A_{ij,j}
$$(p-c-divmat)

## Divergence theorem and integration by parts

An important result for deriving the Finite Element Method is the divergence theorem, also known as Gauss's theorem. It states that integrating the divergence of a vector $\mbf{a}$ on a domain $\Omega$ is equivalent to integrating only at the boundary $\Gamma=\partial\Omega$ of the domain:

$$
\displaystyle\int_\Omega\nabla\cdot\mbf{a}\,\ud\Omega = \int_{\Gamma}\mbf{a}\cdot\mbf{n}\,\ud\Gamma
$$(p-c-divtheoremvec)

where $\mbf{n}$ is the vector normal to the surface $\Gamma$.

We can use this result to arrive at useful **integration by parts** expressions. Starting from a scalar/vector product, integrating over $\Omega$ and employing the derivative product rule $(fg)'=f'g + fg'$ we have:

$$
\displaystyle\int_\Omega\nabla\cdot\left(a\mbf{b}\right)\,\ud\Omega = \int_\Omega\nabla a\cdot\mbf{b}\,\ud\Omega + \int_\Omega a\left(\nabla\cdot\mbf{b}\right)\,\ud\Omega
$$(p-c-prodderivscalarvec)

Now, using Eq. {eq}`p-c-divtheoremvec` but setting $\mbf{a}=a\mbf{b}$ we can substitute the divergence theorem result into the left hand side of Eq. {eq}`p-c-prodderivscalarvec` to get:

$$
\displaystyle\int_\Gamma a\mbf{b}\cdot\mbf{n}\,\ud\Gamma = \int_\Omega\nabla a\cdot\mbf{b}\,\ud\Omega + \int_\Omega a\left(\nabla\cdot\mbf{b}\right)\,\ud\Omega
$$(p-c-intbypartsscalar)

Finally, restructuring gives an equality that will be used in finite element derivations: 

$$
\displaystyle\int_\Omega a\left(\nabla \cdot\bb\right)\,\ud\Omega = -\int_\Omega\nabla a\cdot\bb\,\ud\Omega + \int_\Gamma a\bb\cdot\mbf{n}\,\ud\Gamma
$$(p-c-divtheoremvecfinal)

We can proceed in the exact same way for integrating the divergence of a second-order tensor. In that case the divergence theorem reads:

$$
\displaystyle\int_\Omega\nabla\cdot\mbf{A}\,\ud\Omega = \int_\Gamma\mbf{A}\cdot\mbf{n}\,\ud\Gamma
$$(p-c-divtheoremmat)

and again using the derivative of a product we get to the integration by parts expression:

$$
\displaystyle\int_\Omega\ba\cdot\left(\nabla\cdot\mbf{B}\right)\,\ud\Omega = -\int_\Omega\nabla\ba:\mbf{B}\,\ud\Omega + \int_\Gamma\ba\cdot\mbf{B}\cdot\mbf{n}\,\ud\Gamma
$$(p-c-divtheoremmatfinal)

Check the expression above and make sure you can see that all integrals evaluate to scalars.