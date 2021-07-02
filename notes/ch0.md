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
           $$u_{i} = M_{i1} x_{1} + M_{i2} x_{2} = \sum\limits_{j=1}^{2} M_{ij} x_{j}$$
           for $i = 1, 2$
       
#. Multiplying matrices together and the Kronecker Delta
    a) Generalizing to a $n$-dimensional matrix from above in-line equation.
        $$u_{i} = \sum\limits^{n}_{j=1} M_{ij}x_{j} $$ {#eq:0.13} 
    #) In (\ref{eq:0.10}), $j$ index goes over $M$'s columns and $x$'s rows.
    #) Multiplying matrices (like in (\ref{eq:0.11}), and using \ref{eq:0.13} yields
        $$ p_{i} = \sum\limits_{j=1}^{n} N_{ij}u_{j} \sum\limits_{j=1}^{n}\sum\limits_{k=1}^{n} N_{ij} M_{jk} x_{k} = \sum\limits_{k=1}^{n} P_{ik}x_{k}$$ {#eq:0.14}
    Where $P=NM$ from (\ref{eq:0.11}) is equal to 
    $$ P_{ik} = \sum\limits_{j=1}^{n} N_{ij} M_{jk} $$ {#eq:0.15}
    #) Define identity matrix, $I$ with $I_{ij} = \delta_{ij}$ where $\delta_{ij}$ is the Kronecker delta sybmol : 
    $$ \delta_{ij} = \begin{cases}
                     1, & \text{if $i=j$}\\
                     0, & \text{if $i \neq j$} 
                     \end{cases} $$ {#eq:0.16}
    #) Follows from (\ref{eq:0.15})
    $$ (IM)_{ik} = \Sigma^{n}_{j=1}\delta_{ij}M_{jk} = M_{ik}$$
       Therefore $IM = MI = M$
    #) Can think of Matrix in (\ref{eq:0.12}) like 
    $$ M = \left(\vec{\psi_{(1)}}, ..., \vec{\psi_{(k)}}, ..., \vec{\psi_{(n)}}\right) $${#eq:0.17}
    #) Similarly with $P$ as $n$ different column vectors $\vec{\phi}_{(k)}$, \ref{eq:0.15})
       becomes
    $$ P = \left(\vec{\phi_{(1)}}, ..., \vec{\phi_{(n)}}\right) = NM = \left(N\vec{\psi_{(1)}}, ..., N\vec{\psi_{(n)}}\right) $$ {#eq:0.18}

#. Einstein's repeated index summation
    a) Repeated indices (see \ref{eq:0.15}), instructs to sum over index. In (\ref{eq:0.15})
       $j$ appears twice, called 'dummy indice'. 
    #) $i$ and $k$ appear once and are 'free indices'. They show up as the subscipts in
       $P_{ik}$.
    #) If we understand that repeated indices are summed over, the summation symbol is
       redundant

#. Not Commutative, but associative
    a) Not Commutative : generally $NM \neq MN$
    #) Is associative : $(AB)C = A(BC)$
    $$ NM \neq MN \quad \text{but} \quad (AB)C = A(BC)$$ {#eq:0.19}

#. Transpose
    a) $(M^{T})_{ij} = M_{ji}$
    #) Important theorem:
    $$ (NM)^{T} = M^{T}N^{T} $$ {#eq:0.20}
    #) Proof of (\ref{eq:0.20}) : 
    \begin{align}
       \nonumber ((N M)^{T})_{ij} = (NM)_{ji} = (N_{jk} M_{ki}) = (N_{kj}^{T} M_{ik}^{T}) = \\
       \nonumber \text{arbitrarily switch N and M so indices contract(?)} \\
       \nonumber = (M_{ik}^{T} N_{kj}^{T}) = (M^{T} N^{T})_{ij} 
       \end{align}

#. Trace
    a) Trace is sum of diagonal elements of matrix
    $$ \text{tr} M = \Sigma_{i} M_{ii} = M_{ii} $$          {#eq:0.21}
    #) Important fact, despite $AB \neq BA$, 
    $$ AB \neq BA \quad \text{but} \quad \text{tr} AB = \text{tr} BA$$  {#eq:0.22}
    #) This leads to cyclic property of the trace
    $$ \text{tr} ABC = \text{tr} (AB)C = \text{tr} C(AB) = \text{tr} CAB $$  {#eq:0.23}

#. The inverse
    a) For an ordinary number $m$, it's inverse is $1/m$ such that $m m^{-1} = 1$. 
        #. true if $m \neq 0$
    #) Similar condition must exist for matrices, e.g. $M M^{-1} = I$
    #) If $M$ in (\ref{eq:0.10}) has an inverse, then it is straight forward to solve
    $$ \vec{x} = I\vec{x} = M^{-1}M\vec{x} = M^{-1}\vec{u}$$  {#eq:0.24}
    #) Comparing (\ref{eq:0.7}) to (\ref{eq:0.24})
    $$ M^{-1} = \frac{1}{D} \begin{pmatrix} d  - b\\ -c + a \end{pmatrix}$$ {#eq:0.25}
    where
    $$ D = \frac{1}{ad - bc} $$ {#eq:0.26}
    where $D$ is the determinant of $M$.
    #) IMPORTANT : $M^{-1}$ exists ONLY if $det M = D \neq 0$
    #) By theoretical physics standards, if we can show that a generic 2 x 2 matrix has
       inverse and we can prove that a 3 x 3 has an inverse and show a pattern, then by 
       our standards, we can prove that all matrices have an inverse.
    #) Let 3x3 analogue be : 
    $$ ax + by + cz = u $$ {#eq:0.27}
    $$ dx + ey - fz = v $$ {#eq:0.28}
    $$ gx + hy + iz = w $$ {#eq:0.29}
    #) 3 equations, 3 unknowns. Is solvable. Eliminate $z$ with $i$(\ref{eq:0.27}) - $c$(\ref{eq:0.29}) :
    $$ i(ax + by + cz = u) $$ 
    $$ -c(gx + hy + iz = w) $$
    yields
    $$ iax + iby -cgx - chy = iu - cw$$
    rearrange
    $$ (ia-cg)x + (ib - ch)y = iu - cw$$ {#eq:0.30}
    Also the combo of $i$(\ref{eq:0.28}) - $f$(\ref{eq:0.29}) : 
    $$ i(dx + ey - fz = v) $$ 
    $$ -f(gx + hy + iz = w) $$
    yields 
    $$ (id-fg)x + (ie -fh)y = iv - fw $$ {#eq:0.31}
    #) By eliminating $z$, we've reduced equations (\ref{eq:0.27}), (\ref{eq:0.28}),
       (\ref{eq:0.29}) to two equations : 
    $$ a'x + b'y = u'$$ {#eq:0.32}
    $$ c'x + d'y = v'$$ {#eq:0.33}
    where $a' = (ia-cg), and so forth. Now we can apply the solutions give in (\ref{eq:0.4}),
    (\ref{eq:0.6}) and (\ref{eq:0.7})







