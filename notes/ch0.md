<!--
Compile :
    pandoc -f markdown notes/some_file.md --filter pandoc-crossref -t latex -o some_file.pdf

--
Notes:
    1. http://lierdakil.github.io/pandoc-crossref/
    
-->


<!--
    YAML section
-->
---
title: A Brief Review of Linear Algebra
author: Ali Snedden
date: 2021-04-29
abstract: Notes on the chapter 0 (?) which is before Part 1. It is a review of linear algebra (which I will benefit from).
...
---
header-includes:
  - \hypersetup{colorlinks=true,
            urlcolor=blue,
            pdfborderstyle={/S/U/W 1}}
---
\definecolor{codegray}{gray}{0.9}
\newcommand{\code}[1]{\colorbox{codegray}{\texttt{#1}}}

\maketitle
\tableofcontents
\pagebreak

A Brief Review of Linear Algebra
====================
1. Coupled linear equations
    a) Chicken and Rabbit problem : A farmer counts 7 heads and 22 legs, how many chickens
       and rabbits are in the cage?
        #. System of equations
            * heads : $x + y = 7$
            * legs  : $2x + 4y = 22$
        #. More abstractly : 
            $$ ax + by = u$$            {#eq:0.1}
            $$ cx + dy = v$$            {#eq:0.2}
        #. Eliminating $y$ by multiplying (\ref{eq:0.1}) by $d$ and (\ref{eq:0.2}) by
           $b$ and subtracting (\ref{eq:0.2}) from (\ref{eq:0.1})
            $$ dax - bcx = du - bv $$
        #. Factoring 
            $$ (da - bc)x = du - bv $$  {#eq:0.3} 
        #. Solving for $x$ and separating the dot product 
            $$ x = \frac{du - bv}{ad - bc} = \frac{1}{ad - bc}(d, -b)\begin{pmatrix} u \\ v \\ 
               \end{pmatrix}$$          {#eq:0.4} 
        #. Similarily, we can take the approach of eliminating $x$ by multiplying 
           (\ref{eq:0.2}) by $a$ and (\ref{eq:0.1})  by $c$. Subtracting the two equations
           yields 
           $$ (cb - ad)y = cu -av$$     {#eq:0.5}
           $$ x = \frac{cu - av}{ad - bc} = \frac{1}{ad - bc}(-c, a)\begin{pmatrix} u \\ v \\ 
              \end{pmatrix}$$ {#eq:0.6} 
    #) This is child's play

#. Matrix Appears
    a) Putting together (\ref{eq:0.4}) and (\ref{eq:0.6}), one gets our first matrix
       $$\begin{pmatrix} x \\ y \\ \end{pmatrix} =
         \frac{1}{ad - bc}\begin{pmatrix} du - bv \\ -cu + av \end{pmatrix} =
         \frac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix} \begin{pmatrix} u \\ v \end{pmatrix}$$ {#eq:0.7}
    #) Another example of multiplying a matrix on a column vector
       $$\begin{pmatrix} a & b \\ c & d \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} =
        \begin{pmatrix} ax + by \\ cx + dy \end{pmatrix}$$ {#eq:0.8}
    #) Rewritten (\ref{eq:0.8})
       $$\begin{pmatrix} a & b \\ c & d \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} =
        \begin{pmatrix} u \\ v \end{pmatrix}$$ {#eq:0.9}
    #) Let $M = \begin{pmatrix} a & b  \\ c & b  \end{pmatrix}$ and
       $\vec{x} = \begin{pmatrix} x \\ y \end{pmatrix}$ and 
       $\vec{u} = \begin{pmatrix} u \\ v \end{pmatrix}$ then
        $$ M \vec{x} = \vec{u}$$ {#eq:0.10}

#. Turning the problem around
    a) Think of $M$ transforming $\vec{x} \rightarrow \vec{u}$
    #) What mappens when we introduce another matrix, $N$, to transform $\vec{u}$?
    $$\vec{p} = N\vec{u} = N M \vec{x} = P \vec{x}$$ {#eq:0.11}
    #) Dispose with $\vec{p}$, $\vec{x}$ and $\vec{u}$ altogether, just consider the relation
       between $P = N M$.  
        #. Multiplying matrices is a central theme of group theory
        #. Introduce indices. 

#. Appearance of indices and rectangular matrices
    a) Write $M = \begin{pmatrix} M_{11} & M_{12} \\ M_{21} & M_{22} \end{pmatrix}$
        #. Using $M_{ij}$ for the $i$'th row and the $j$'th column
    #) Consider, $M_{31} = g$ and $M_{23} = f$ in the below matrix
        $$M = \begin{pmatrix} a & b & c \\ d & e & f \\ g & h & i\end{pmatrix}$$ {#eq:0.12}
    #) Let $\vec{x} = \begin{pmatrix} x_{1} \\ x_{2} \end{pmatrix}$ and $\vec{u} = \begin{pmatrix} u_{1} \\ u_{2} \end{pmatrix}$ 
        #. Can then rewrite (\ref{eq:0.10}) as 
           $$u_{i} = M_{i1} x_{1} + M_{i2} x_{2} = \Sigma_{j=1}^{2} M_{ij} x_{j}$$
           for $i = 1, 2$
       
#. Multiplying matrices together and the Kronecker Delta
    a) Generalizing to a $n$-dimensional matrix

