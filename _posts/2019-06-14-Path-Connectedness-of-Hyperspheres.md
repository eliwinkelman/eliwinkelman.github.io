---
published: true
---

We can show that $S^n$ is path connected once we have the right groundwork:

1. Show that $S^n - \{N\}$ is homeomorphic to $\mathbb{R}^{n-1}$ through the stereographic project.
2. Show that $\mathbb{R}^n$ is path connected.

Then the proof follows by supposing that two distinct points in $S^n$ are not path connected. We can pick another distinct point, $N$, and remove it from the space, creating a space $S^n - \{N\}$ which is homeomorphic to $\mathbb{R}^n$ and therefore must be path connected. So there must exist a path between our two distinct points.

### Path Connectedness

Definition: A path in a topological space $X$ between points $p, q \in X$ is a continuous function $\gamma : [0, 1] \rightarrow X$ such that $\gamma(0) = p$ and $\gamma(1) = q$.

Definition: A topological space $X$ is path connected if for any two points $p, q \in X$ there is a path $\gamma$ between them.

### The Stereographic Projection

The stereographic projection is a projection of the n-sphere onto $\mathbb R^{n-1}$.


<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Stereoprojzero.svg/1280px-Stereoprojzero.svg.png" width="400" height="400" align="middle"/>

Joshua Davis [Distributed under CC BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/)



Pick a north pole $N$ of $S^n \subset \mathbb{R}^{n}$. Then the projection of the point $Q \in S^n-{N}$ onto the hyperplane $H \subset \mathbb R^{n}$ is the intersection of $\overline{NQ}$ with $H$.

In Cartesian Coordinates this is given by

$$P_i = \frac{p_i}{1-p_0}$$

where here $N=(1, 0, 0 ... 0)$, $(p_0, p_1, ... p_n)$ are the coordinates of the point on the n-sphere and $(P_0, P_1, ... P_n)$ are the points on the projected hyperplane.

This function is continuous, and it has a continuous inverse.

Therefore, this definies a homeomorphism between $S^n - \{N\}$ and $\mathbb R^{n-1}$ Note that the choice of the point $N$ is arbitrary.

### Path Connectedness of $\mathbb{R^n}$

Theorem: If $X, Y$ are path connected, then so is $X \times Y$.

Proof: Let $p, q \in X \times Y$ be points. Then $p = (x_1, y_1)$ and $q = (x_2, y_2)$. Since $X$ is path connected, there is a path $\gamma_1$ from $x_1$ to $x_2$. Similarly, there is a path $\gamma_2$ between $y_1$ and $y_2$. Therefore $\gamma = (\gamma_1, \gamma_2)$ is a path in $X \times Y$ between $p$ and $q$. $\square$

Theorem: $\mathbb{R}$ is path connected.

Proof: Let $p, q \in \mathbb{R}$ be distinct points. Then $p = (x_1, y_1)$ and $q = (x_2, y_2)$. Observe that the function 
$$\gamma(t) = (
\frac{1}{x_2-x_1}(t+x_1), \frac{1}{y_2-y_1}(t+y_1))$$ 
is a path between $p$ and $q$. $\square$

### Path Connectedness of $S^n$

Theorem: $S^n$ is path connected for $n \geq 1$.

Proof: Let $p, q \in S^n$ be distinct points and suppose they are not path connected. Then let $N$ be a third distinct point in $S^n$. $S^n - \{N\}$ is homeomorphic to $R^{n-1}$ and therefore path connected, so there must be a path from $p$ to $q$. Thus $S^n$ is path connected.
