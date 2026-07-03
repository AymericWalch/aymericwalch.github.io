---
title: 'Research statement'
url: "/research/"
---

Here is a summary of my works, and of my current research projects.
I am very open to discussions and collaborations ~~in the limits of my overwhelmed postdoctorant time schedule~~, 
so feel free to reach out to me if you have similar research interests.

## 1. Quantitative semantics and Taylor expansion

### Analytic maps and Taylor expansion in quantitative semantics of Linear Logic.

Quantitative semantics of Linear Logic are based on the idea that types should be represented by sets of vectors
and programs by analytic map. The [Differential Lambda Calculus](https://www.sciencedirect.com/science/article/pii/S030439750300392X)
discovered by Ehrhard and Regnier
pushes this analogy to a formal correspondence between differentiation of analytic map and 
the analysis of the resource sensitivity of programs.

However, only a few quantitative semantics are models of the differential lambda calculus, because 
this calculus forces the model to 
features arbitrary sums (this coresponds on the side of computations to non-determism).
This restricted scope contrasts with the ubiquity of analytic maps in quatitative semantics.
I worked during my thesis with [Thomas Ehrhard](https://www.irif.fr/~ehrhard/) on **Coherent Differentiation**, 
a generalization of DiLL to a whole new range of models of Linear Logic 
(coherence spaces, probabilistic coherence spaces, etc.). 
The main contribution of my thesis was to revisit Taylor expansion in that new setting.

> Ehrhard T, Walch A. **Coherent Taylor expansion as a bimonad**. Mathematical Structures in Computer Science. 2025. The preprint is available [here](https://hal.science/hal-04225534/document)

> Tasson C, Walch A, **Absolute convergence and Taylor expansion in web based models of Linear Logic**, [preprint](https://arxiv.org/abs/2603.25215)

The key ingredient of this coherent theory of differentiation and of Taylor expansion is the use of **partial sums** instead of total sums. 
In hindsight, this seems very obvious, since the standard theory of analytic maps in analysis already features 
such partiality. 

---

I am currently investigating the **syntactic** counterpart of these partial sums. I believe in
particular that they are deeply related to the proofs of normalization of Taylor expansion in 
the resource calculus.

---


### Web models of Linear Logic

Web models are a wide class of quantitative semantics of Linear Logic that are all built with a method based on orthogonality. They notably include coherence spaces, probabilistic coherence spaces, (weighted) relational model, finiteness spaces, Köthe spaces. It is well known that those models are all built using the same method, but there was no formal result that tied those models together. 

I recently discovered a generic method to build web models that unify all the aforementionned constructions. This method can be found in the first part of my paper 
> Tasson C, Walch A, **Absolute convergence and Taylor expansion in web based models of Linear Logic**, [preprint](https://arxiv.org/abs/2603.25215)

that I wrote with [Christine Tasson](https://www.lip6.fr/Christine.Tasson/). The point of this method is not to be 
as general as possible, but rather to follow each individual model very tightly. As such, this construction 
provides a very convenient toolbox of examples to design theories on categorical semantics of Linear Logic.

---

In particular, I am currently trying to characterize which of these web models are Lafont (that is, the exponential is given 
by the cofree commutative comonoid). I found with [Christine Tasson](https://www.lip6.fr/Christine.Tasson/) and 
[Guillaume Geoffroy](https://geoffroy.re/fr/) a characterization that is yet again based on Taylor expansion.
This work is going smoothly and should be published soon.

---


## 2. Categorical differentiation

[**Differential categories**](https://www.math.mcgill.ca/rags/difftl/MSCS-Differential_Categories.pdf) were initially introduced by Blute Cockett and 
Seely in order to provide an axiomatization of models for Ehrhard and Regnier's
differential lambda calculus.
This line of work on the categorical properties of differentiation then drifted apart from Linear Logic, with the successive 
introduction of two concepts.
1. [Cartesian differential categories](http://www.tac.mta.ca/tac/volumes/22/23/22-23abs.html), that provides an axiomatic description of the differential calculus in categories that are not necessarily models of Linear Logic.
2. [Tangent categories](https://link.springer.com/article/10.1007/s10485-013-9312-0), that generalizes cartesian differential categories to differential geometry.

The study of derivatives in categories thus became a research field on its own called **categorical differentiation**.
While still deeply related to Linear Logic, categorical differentiation has also 
deep connections with synthetic differential geometry, automated differentiation and the abelian functor calculus.

### Categorical properties of derivatives

A substantial part of my work on coherent differentiation (see the related section)
was to relate our new axiomatization with the rest of the work on categorical differentiation.
In particular, I noticed in

> Thomas Ehrhard, Aymeric Walch, **Cartesian Coherent Differential Categories** in 2023 38th Annual ACM/IEEE Symposium on Logic in Computer Science (LICS), Boston, MA, USA, 2023. The preprint is available [here](https://arxiv.org/abs/2303.06952)

that the properties of the differential calculus (chain rule, linearity of the derivative, Schwarz theorem) are in **one to one** correspondence with functoriality and naturality equations 
on the **tangent bundle** operator. 
For that reason, I strongly believe that every property of the derivative in cartesian differential categories should be expressed instead as 
categorical properties on the tangent bundle functor.

### Categorical properties of Taylor expansion

The key technical argument of my work on Taylor expansion in models of Linear Logic (see the related section)

> Ehrhard T, Walch A. **Coherent Taylor expansion as a bimonad**. Mathematical Structures in Computer Science. 2025. The preprint is available [here](https://hal.science/hal-04225534/document)

was to generalize the tangent bundle operator to some kind of **Taylor bundle** operator, that computes the whole Taylor expansion of a map 
instead of simply its tangent. What really struck me in this work is that this Taylor bundle enjoys the exact same 
categorical properties as the tangent bundle, even though its underlying combinatorics is clearly more complex.
In order to understand the properties of this Taylor bundle functor, I proved in the following paper 

> Aymeric Walch, **Compositional Taylor expansion in cartesian differential categories** in 2025 40th Annual ACM/IEEE Symposium on Logic in Computer Science (LICS), Singapore, 2025. The preprint is available [here](https://arxiv.org/abs/2502.09066)

that every cartesian differential category features such Taylor expansion. I avoided the use of **very heavy** combinatorics by using the categorical 
properties of the tangent bundle, instead of the properties of the derivative itself.

--- 

I would like to revisit the Taylor bundle functor in the setting of tangent categories. I expect to find here a categorical axiomatization of jet bundles, as well as a link with the notion of higher order dual numbers used in synthetic differential geometry.

---


## 3. Solving ODEs lazily with Taylor expansion

I hoped in a project started by [Xavier Thirioux](https://pagespro.isae-supaero.fr/xavier-thirioux/). The goal of this project is to compute approximations of solutions of ODEs using Taylor polynomials. The key feature of this approach is its **laziness**: the computation of the approximation will build up the Taylor polynomial coefficient by coefficient, meaning that this computation can be interrupted at any time to yield a usable solution.

This lazy paradigm is particularly well suited for embedded systems in which solutions have to be computed in real time 
(to predict the trajectory of a plane for instance), and in which the available computational resources are limited. 

There is a caveat though: Taylor expansion are great local approximations, but tends to diverge very sharply from the real solution after some time.
To make sure that the solver does not yield a broken value, Xavier devised a method to compute formal bounds on the error of the approximation based
on fixed point iteration. 

---

I am currently working on this project with Xavier Thirioux and Christine Tasson, stay tuned for further development.

---
