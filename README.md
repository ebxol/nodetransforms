# Solver for Relative Sequential Transformations

*E.B. "Xoleras" de Cruz*

### Problem Statement
Define a transformation tree to be a tree $G$ where each vertex holds rotation and translation data $R$ and $T$ of an axis in space, and the final orientation of said axis is the sequence of rotations and transformations of its parent vertices up to the root.

For example, given a transformation tree $G$, there is a path from the root to any vertex ($N_0$ to $N_i$). The axis represented by $N_i$ has a rotation of $R_0 R_1 R_2 ... R_{i-1}$ where each $R$ is a rotation matrix, and a translation of $v_0 + R_0 v_1 + R_1 v_2 + ... + R_{i-1} v_i$

...

Given a tranformation tree $G$ and a vertex $g$, determine the final absolute translation expressed as a rotation matrix and a vector.

Furthermore, we can solve the following intermediate problem:

Given an axis with a particular rotation and translation, and a vertex $g$ of $G$, find the orientation $<\hat{R}, \hat{T}>$ so that if the axis were to be a child vertex of $g$, then it would remain in its original place. In other words its original orientation would be the same as its orientation within the tree structure.

### Solutions

For rotation:


$\hat{R} = (R^*)^{-1}R$

For translation:

$T^{\ast}$ is some rotated vector $R^{\ast} \vec{v}$ and there is a vector $\vec{x}$ that will yield the original translation $T$, that is $R^*(\vec{v} + \vec{x}) = T$, therefore


$T^{\ast} + R^{\ast} \vec{x} = T$

$R^{\ast} \vec{x} = T - T^*$

Which is a linear system and we know it has a single nonzero solution because the axes are linearly independent and we assume the tree structure is nontrivial; that is, it concerns nodes with non-identity translations.
