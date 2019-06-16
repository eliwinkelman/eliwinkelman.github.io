---
published: true
---
## The Path Connectedness of $S^n$


\subsection {Path Connectedness}

Definition: A path in a topological space $X$ between points $p, q \in X$ is a continuous function $\gamma : [0, 1] \rightarrow X$ such that $\gamma(0) = p$ and $\gamma(1) = q$.

Definition: A topological space $X$ is path connected if for any two points $p, q \in X$ there is a path $\gamma$ between them.

\subsection {The Stereographic Projection}

The stereographic projection is a projection of the n-sphere onto $\mathbb R^{n-1}$.

![Stereographic Projection Illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Stereoprojzero.svg/1280px-Stereoprojzero.svg.png "Stereographic projection of the unit sphere from the north pole onto the plane z = 0, Joshua Davis") Joshua Davis [Distributed under CC BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/)

Pick a north pole $N$ of $S^n \subset \mathbb{R}^{n+1}$. Then the projection of the point $Q \in S^n-{N}$ onto the hyperplane $H \subset \mathbb R^{n+1}$ is the intersection of $\overline{NQ}$ with $H$.

In Cartesian Coordinates this is given by
\[P_i = \frac{p_i}{1-p_0}\]
where here $N=(1, 0, 0 ... 0)$, $(p_0, p_1, ... p_n)$ are the coordinates of the point on the n-sphere and $(P_0, P_1, ... P_n)$ are the points on the projected hyperplane.

This function is continuous, and it has a continuous inverse

Therefore, this definies a homeomorphism between $S^n - {N}$ and $\mathbb R^n$

\subsection{Path Connectedness of $\mathbb{R^n}$}

Theorem: If $X, Y$ are path connected, then so is $X \times Y$.

Proof: Let $p, q \in X \times Y$ be points. Then $p = (x_1, y_1)$ and $q = (x_2, y_2)$. Since $X$ is path connected, there is a path $\gamma_1$ from $x_1$ to $x_2$. Similarly, there is a path $\gamma_2$ between $y_1$ and $y_2$. Therefore $\gamma = (\gamma_1, \gamma_2)$ is a path in $X \times Y$ between $p$ and $q$. $\square$

\subsection{Path Connectedness of $S^n$}
Theorem: $S^n$ is path connected for $n \geq 1$.

Proof: Let $p, q \in S^n$ be distinct points and suppose they are not path connected.

