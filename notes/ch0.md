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
            $$ ax + by = u$$ {#eq:0.1}
            $$ cx + dy = v$$ {#eq:0.2}
        #. Eliminating $y$ by multiplying Eq. \ref{eq:0.1} by $d$ and Eq. \ref{eq:0.2} by
           $b$ and subtracting Eq. \ref{eq:0.2} from Eq. \ref{eq:0.1} 
            $$ dax - bcx = du - bv $$
        #. Factoring 
            $$ (da - bc)x = du - bv $$ {#eq:0.3} 
        #. Solving for $x$ and separating the dot product 
            $$ x = \frac{du - bv}{da - bc} = \frac{1}{ad - bc}(d, -b)\begin{pmatrix}
                                                                    u \\
                                                                    v \\ 
                                                                    \end{pmatrix}$$ {#eq:0.4} 
            



