---
layout: post
author: robw
title: Lipschitz continuity
abstract: Whilst teaching an electrical engineering course for the first time, I was forced to revisit much of what I thought I knew about electrical circuit analysis. As part of this process I started writing this cheat sheet to electrical circuit analysis. More to follow!
image: /assets/images/electrical.jpg
numbered: false
---

Over the last year or so I have seen Lipschitz continuity increasingly discussed in deep learning literature. It has a central role to play in Generative Adversarial Networks: it can be used to identify training instabilities in GANs training; has been proposed as a possible fix; and has a central role to play in the Wasserstein GAN formulation. It has also been used to improve models robustness to adversarial attack as well as for learning smooth latent spaces in auto-encoder settings, and has cropped up in several papers I have read on normalising flows.

In this post, I am going to provide a fairly high level overview of what Lipschitz continuity is, what benefits imposing lipschitz continuity on deep models might bring, and how this is achieved.

## What is it?
So before going any further, what is Lipschitz continuity? Lets start with continuity. A continuous function $f: \mathbb{R}^n \rightarrow \mathbb{R}^m$ does not have any abrupt changes in value. The least restricted types of continuous functions are referred to as _absolutely continuous_ which is often what we think of when we say "continuous".  In the case of a single real variable they correspond to all functions that can be drawn without taking pen from paper. 

Lipschitz continuous functions have additional constraints on how quickly their values are able to change. Precisely we have...

Lipschitz Continuity
: Let $G$ be an open convex subset of $\mathbb{R}^n$. A function $f: G \to \mathbb{R}$ is *Lipshitz continuous* if there exists a constant $K \geq 0$ such that,
 
$$\|f(y)-f(x)\| \leq K\|y - x\| \quad \forall x, y \in G$$

>In general this is defined for all norms (and not necessarily the same) in $\mathbb{R}^n$ and  $\mathbb{R}^m$. The Lipschitz constant $K$ will vary depending on our choice of norm.

The visualisation below (shamelessly taken from [wikpedia](https://en.wikipedia.org/wiki/Lipschitz_continuity)) illustrates this constraint. To be lipschitz continuous the function must remain outside of the white cone at every point in its domain. Larger values of $K$ will result in wider cones and therefore a stricter version of continuity. Provided that a cone can be found for a particular $K$ satisfying the above condition the function $f$ is said to be lipschitz continuous with lipschtiz constant $K$.


<img src="https://upload.wikimedia.org/wikipedia/commons/5/58/Lipschitz_Visualisierung.gif" alt="drawing" width="350"/>
_visualisation of a lipschitz continuous function_

Intuitively the lipschitz continuity can be seen to be constraining how quickly a function value is allowed to change. If the function $f$ is also differentiable we have


Lipschitz continuity of a differentiable function
: If $f$ is also (uniformally) continuous and differentiable for
 all $x$ in $G$ then $f$ is $K$-Lipschitz continuous iff $
 \|\| \nabla 
  f (x) \| \| \leq K \ \forall  \ x \in G$

That is, a differentiable function is K-lipshitz if its gradient at any point in its domain is bounded by $K$. From this we can see that our earlier intuition is exactly correct if $f$ is differentiable.

The proof of the above result follows from the mean value theorem
 (see appendix). As $f$ is continuous and differentiable for every
  $x,y \in G$ there exists a $c$ such that $\|\|f(y)- f(x)\|\| \leq
    \|\| \nabla f (z) \|\| \cdot \|\|x - y\|\|$. As $z = (1-c)x + cy$
     then $z$ will also lie in $G$ for all $x,y$ (assuming that $G$ is a convex set as before). Strictly speaking (I think) this condition only holds if the function is also _uniformly_ continuous. This is a slightly stricter form of continuity discussed in more detail at the end of this blog post. 

>Formally defining continuity for a general function $f: X \rightarrow Y$ depends on the type of spaces $X$ and $Y$ and what mathematical machinery we have available to define closeness. Different definitions can therefore be given and used depending on how strict a version of continuity we wish to consider. This is discussed in slightly more depth at the end of this blog post. For the rest of this post we will specifically be considering functions over normed vector spaces $X = \mathbb{R}^n$ and $Y = \mathbb{R}^n$ with norms $\| \cdot \|$.

## So why is lipschitz continuity useful?
There are several problem domains in which lipschitz continuity is important.

### Generative Modelling
Given a dataset of observations $\mathcal{D} = \{ x_k \}_{k=1
}^K$
 of observations $x \in \mathbb{R}^n$ we aim to approximate the
  true distribution $p_x^\*(x)$ with an approximation $p_x(x
   \| \theta)$ such that $p_x^\* \approx p_x$. Several approaches
    could be used here:
1. __Gans__: In this case we implicitly capture $x \sim p_x(x
 \| \theta)$ as, $$z \sim p_z(z) \quad x = f_\theta(x)$$ using a
  neural network $f_\theta$ to a transform a base distribution $p_z(z)$ to $p_x^\*(x)$.

In unsupervised representation learning, given a dataset $\mathcal{D} = \{ x_k \}_{k=1}^K$ of observations $x \in \mathbb{R}^n$ we aim to learn a lower dimensional feature representation $z \in \mathbb{R}^m$ with $m < n$. This can be achieved using an auto-encoder architecture,
$$\hat{x} = d_\theta (z) \quad z = e_\theta(x) $$ with parameters $\theta$ which are determined by maximising $$\mathcal{L}(\theta ; x) = \mathcal{L}_x(\hat{x}; x) + \lambda \mathcal{L}_z(z ; x)$$. Here $\mathcal{L}_x$ is some form of reconstruction loss (eg. MSE, GAN etc.) ensuring that $z$ contains as much information as is necessary to successfully reconstruct $x$ and  $\mathcal{L}_z$ is a regularisation term designed to provide $z$ with some particular properties. 

using a neural network $z = e_\theta(x)$ before using $z$ to recreate the original image $x$ as $\hat{x} = d_\theta (z) = (d_\theta  \circ e_\theta)(x)$. Both networks are then trained to maximise the loss $$\mathcal{L}(\theta ; x) = \mathcal{L}_x(\hat{x}; x) + \lambda \mathcal{L}_z(z ; x)$$ where $\mathcal{L}_x$ is some form of reconstruction loss (eg. MSE, GAN etc.) and



## Why is enforcing lipschitz continuity useful?
There are several applications where enforcing a function to be $K$ lipschitz is useful:
- Generative Modelling
	- Two samples generated from similar latent variables should be similar to one another
	- By enforcing lipschitz constraints using GP and spectral normalisation it is possible to learn smooth latents with a deterministic autoencoder
	- [From Variational To Deterministic Autoencders](https://openreview.net/pdf?id=S1g7tpEYDS)
- Stabilising GAN Training
	- Enforcing 1-lipschitz continuity of the discriminator is essential for Wasserstein GAN which (supposedly) helps with stabilising training.
	- Other methods have also looked at using Lipschitz continuity as a way of regularising the discriminator even before the Wasserstein GAN paper came out.
- Identifying Gan training instability
	-  [BigGan](https://arxiv.org/pdf/1809.11096.pdf) was the first gan network architecture to generalise to high resolution images
	- Part of their solution lied in tracking the largest singular values of the network during training; empirically training becomes unstable when the singular values become very large
- Adversarial attack
	- A network given near identical inputs should produce near identical outputs
	- Unfortunately this is not the case for many neural network architectures

> __Case Study: The Wasserstein GAN__
>  We have samples from $\mathbb{P}$ and want to learn a distribution $\mathbb{Q}_\theta$ which approximates this. But how do we ensure that $\mathbb{P}$ and $\mathbb{Q}_\theta$ are close to another. Several options exist:
>  1. Minimise $d_{KL}(\mathbb{P} || \mathbb{Q}_\theta)$ divergence between $\mathbb{P}$ and $\mathbb{Q}_\theta$. This is equivalent to maximising the log likelihood
>  2. Minimise the $d_{JS}(\mathbb{P} || \mathbb{Q}_\theta)$. This is the same as using the vanilla GAN formulation. Eg.
>  
> The problem is that neither of these metrics are meaningful when the domain of $\mathbb{P}$ and $\mathbb{Q}_\theta$ are disjoint. And at the beginning of training this is almost certainly going to be the case!
> 
> To fix this problem [Wasserstein GAN]() proposes to use the Wasserstein distance between $\mathbb{P}$ and $\mathbb{Q}_\theta$ which does not necessitate that $\mathbb{P}$ and $\mathbb{Q}_\theta$ are overlapping. The Wasserstein distance is also known as the Earth Mover distance; it can be thought of as finding the solution that minimises the amount of work needed to convert one pile of earth into another. Using neural networks the Wasserstein distance $d_{W}(\mathbb{P} || \mathbb{Q}_\theta)$ can be approximated as,
> $$\hat{W}\left(\mathbb{P}, \mathbb{Q}_{\theta}\right)=\hat{\mathbb{E}}_{x \sim \mathbb{P}}\left[f_{\phi}(x)\right]-\hat{\mathbb{E}}_{y \sim \mathbb{Q}_{\theta}}\left[f_{\phi}(y)\right]$$
> with one additional caveat: _the function $f$ must be lipschitz continuous_. The actual lipschitz constant does not matter here. It is just a scaling. But enforcing  lipschitz continuity is essential.

## How is Lipschitz continuity enforced?
In the literature to date there are two main ways of enforcing lipschitz continuity. The first is to explicitly limit the maximum size of the gradient of a function by introducing a [gradient penalty](https://arxiv.org/pdf/1704.00028.pdf) term into the loss and was originally introduced as a better way of enforcing the lipschitz constraint of Wasserstein GANs:

$$ \mathcal{L(\theta)} = \mathcal{L}_{\text{original}}(\theta) + \lambda (||\nabla_x f_{\theta}(x)|| - K)^2$$

The second method relies on [spectral normalisation](https://arxiv.org/pdf/1802.05957.pdf). Choosing $|| \cdot || = || \cdot ||_2$ we can enforce $K$-lipschtiz continuity by ensuring:

$$ \text{sup}_{x \in G} || \nabla f (x) ||_2 =  \text{sup}_{x \in G} \sigma_\text{max}( \nabla f (x)  ) < K $$

Considering neural networks composed of layers of linear transformations followed by non-linear activations the lipchitz continuity of each layer can be enforced by limiting the maximum singular value of each weight matrix $\sigma(\mathbf{W})$. If additionally each non-linearity is K-lipschitz (true for most common activations such as ReLU and Tanh) then the composition of multiple layers will also be (weakly) K-lipshitz.

Which is better remains to be seen. The former relies on hyper parameter sweep of the gradient penalty $\lambda$ above. The latter enforces K-lipshitz constraints only weakly; a significantly smaller $K$ than desired will result in a network with lower capacity.

## Useful Resources
- Papers
	- [From Variational to Deterministic AutoEncoders](https://openreview.net/pdf?id=S1g7tpEYDS)
		- A paper applying lipshitz complaints to learning smooth latent spaces for generative modelling
	- Spectral Normalisation
		- [Spectral Norm Regularization for Improving the Generalizability of Deep Learning](https://arxiv.org/pdf/1705.10941.pdf)
			- The original paper formulating spectral normalisation
		- [Spectral Normalisation for Generative Adverserial Networks](https://arxiv.org/pdf/1802.05957.pdf)
			- A follow up paper
	- [Wasserstein GAN](https://arxiv.org/pdf/1701.07875.pdf)
	- [Gradient Penalty]((https://arxiv.org/pdf/1704.00028.pdf)
	- [A large Scale Stufy on Regularization and Normalization in GANS (2019)](http://proceedings.mlr.press/v97/kurach19a/kurach19a.pdf)
		- Good summary of current state of the art
	- [BigGan](https://arxiv.org/pdf/1809.11096.pdf)
		- Uses singular values to detect training instability
- Blogs
	- Wasserstein GAN
		- [Flavors of Wasserstein GAN - Casey Chu](http://caseychu.io/posts/flavors-of-wasserstein-gan/)
		- [From GAN to WGAN - Lilian Weng](https://lilianweng.github.io/lil-log/2017/08/20/from-GAN-to-WGAN.html#wasserstein-gan-wgan)
- PDFs
	- [A review of multi-variable calculus](https://sites.math.washington.edu/~burke/crs/408/notes/review/calc_rev.pdf)
	- [Generalizing The Mean Value Theorem](https://ocw.mit.edu/courses/mathematics/18-01sc-single-variable-calculus-fall-2010/unit-2-applications-of-differentiation/part-c-mean-value-theorem-antiderivatives-and-differential-equations/session-34-introduction-to-the-mean-value-theorem/MIT18_01SCF10_ex34sol.pdf)
	- [Elements of Multivariable Calculus](https://sites.math.washington.edu/~burke/crs/408/notes/Math408_Spring2014/calc_rev408.pdf)
	- [Matrix Cookbook](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf)
- Wikipedia
	- [Mean value theorem](https://en.wikipedia.org/wiki/Mean_value_theorem)
	- [Cauchy-Schwarz Inequality](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Schwarz_inequality)
	- [Lipshitz continuity](https://en.wikipedia.org/wiki/Lipschitz_continuity)

## Appendix
### Types of Continuity
What we mean by a continuous function $f: X \rightarrow Y$ depends on what sort of spaces  $X$ and $Y$ and so what machinery we have at our disposal with which to define closeness between elements. For topological spaces this is done by considering set membership and neighbourhoods resulting in a very general but less useful and intuitive definition of continuity, with no guarantee on size of neighbourhoods. For this we need to define closeness using a metric $d(x_1, x_2)$. We are able to define continuity in different ways depending on how close we want close to be, moving from absolutely to uniformly to Lipschitz continuous. 
 
#### Continuity on Topological Spaces
 For a function $f : X \rightarrow Y$ between two _topological_ spaces $X$ and $Y$, $f$ is continuous if for every $x$ and $y = f(x)$ there is a neighbourhood $U \in \mathcal{N}_x(x)$ mapping to a set $f(N_x) \sub V$ contained in a neighbourhood $V \in \mathcal{N}_y(y)$.  But there is no guarantee on the size of the neighbourhood $V$ - it just has to exist.

![enter image description here](https://upload.wikimedia.org/wikipedia/commons/a/a7/Continuity_topology.svg)
_A visualisation of continuity defined on topologies with $U=N_x$ and $V=N_y$ taken from [wikipedia](https://en.wikipedia.org/wiki/Continuous_function#Continuous_functions_between_metric_spaces)_

#### Continuity on Metric Spaces
If the spaces $X$ and $Y$ also have _metrics_ then continuity provides certain guarantees on the size of $N_y$. A function $f: X \rightarrow Y$ between two _metric_ spaces $(X, d_x)$ and $(Y, d_y)$ is
- _absolutely continuous_ for every $x_1$, for every $\epsilon > 0$ there exists a $\delta > 0$ such that $$d_x(x_1, x_2) <\delta \implies d_y(f(x_1), f(x_2)) < \epsilon \quad \text{for all} \quad x_2 \in X$$ 
- _uniformly continuous_ if, for every $\epsilon > 0$ there exists a $\delta > 0$ such that $$d_x(x_1, x_2) <\delta \implies d_y(f(x_1), f(x_2)) < \epsilon \quad \text{for all} \quad x_1, x_2 \in X$$

For a continuous function the maximum distance $\delta$ between $f(x)$ and $f(y)$ is allowed to change with $x$ and $y$, whilst in the uniform case this is not the case. Uniform continuity is a stricter requirement: all uniformly continuous functions are continuous, but the converse is not always true. Below we can see a visualisation of an absolutely continuous function (blue) alongside a uniformly continuous function (red). In the uniform case it is possible to find a $\delta$ for any choice of $\epsilon$ such that the maximum difference in the function will always be less than $\epsilon$ for all $|x - y| < \delta$. This is not true in the other case.

![enter image description here](https://upload.wikimedia.org/wikipedia/commons/b/b1/Continuity_and_uniform_continuity_2.gif)
_A visualisation of continuity vs uniform continuity taken from [wikipedia](https://en.wikipedia.org/wiki/Uniform_continuity). For a uniformly continuous function it is possible to find an $\epsilon$ and $\delta$ that works for all $x$ whilst in the continuous case $\epsilon$ and $\delta$ must change with $x$. The continuous case (blue) escapes its epsilon bound as $x \rightarrow 0$_

It might seem fairly unintuitive that there are certain cases where it is impossible to choose a fixed $\delta$ for all $x_1, x_2 \in X$. In this case an example showing when this is impossible might be helpful. The function $f(x) = x^2$ for $x \in \mathbb{R}$ is absolutely continuous but _not_ uniformly continuous. In order to prove that $f(x)$ is uniformly continuous we need to need to find a $\delta$, such that for every $\epsilon > 0$ we have, $$|x - y| < \delta \implies |x^2 - y^2| < \epsilon$$. But if we choose $y=x + \delta / 2$ such that $|y - x| = \delta / 2 < \delta$ so that the LHS holds, we now need,  substituting for $y$ in the RHS, expanding and cancelling terms gives $|x\delta - \delta^2 / 4| < \epsilon$. This condition needs to hold for all $x \in \mathbb{R}$. But no matter how large we make $\epsilon$ we will always be able to make $x$ big enough such that this condition no longer holds. As a result the function $f(x) = x^2$ is not uniformly continuous. $\blacksquare$

#### Lipschitz continuity
A function $f: X \rightarrow Y$ between two _metric_ spaces $(X, d_x)$ and $(Y, d_y)$ is _lipschitz continuous_ if there exists a $K > 0$ such that $$d_y(f(x_1), f(x_2)) < K d_x(x_1, x_2) \quad  \text{for all} \quad x_1, x_2 \in X$$. It is a strictly stronger definition of continuity than uniform continuity; all lipschitz continuous functions are uniformly continuous but the reverse is not always true. 



### Singular Value Decomposition 
Any $n \times m$ matrix $\mathbf{A}$ can be written as:

$$\begin{array}{c}{\mathbf{A}=\mathbf{U D V}^{T}} \\ {\mathbf{U}=\text { eigenvectors of } \mathbf{A} \mathbf{A}^{T} \quad n \times n} \\ {\mathbf{D}=\sqrt{\operatorname{diag}\left(\operatorname{eig}\left(\mathbf{A} \mathbf{A}^{T}\right)\right)} \quad n \times m} \\ {\mathbf{V}=\text { eigenvectors of } \mathbf{A}^{T} \mathbf{A} \quad m \times m}\end{array}$$

Note:
- The diagonal elements of $\mathbf{D}$ are the singular values of  $\mathbf{A}$
- If $\mathbf{A}$ is **square and symmetric** then $[\mathbf{A}]=[\mathbf{V}][\mathbf{D}]\left[\mathbf{V}^{T}\right]$  (i.e singular value decomposition is equal to the eigenvalue decomposition
- The two norm of a matrix is given by the square root of the largest singular value of a matrix: 
	$$\|\mathbf{A}\|_{2}=\sqrt{\max \operatorname{eig}\left(\mathbf{A}^{H} \mathbf{A}\right)}$$

### Mean Value Theorem
Let $G$ be an open convex subset of $\mathbb{R}^n$ and let $f: G \to \mathbb{R}$ be a differentiable function then there exists $c \in (0, 1)$ such that, 

$$f(y)- f(x) = (y - x)^\top \nabla f (z), \quad \text{with}  \quad z = (1-c)x + cy$$

Equivalently using the Cauchy-Schwarz inequality ($||u \bullet v || \leq ||u|| \bullet ||v||$):

$$||f(y)- f(x)|| \leq ||x - y|| \cdot || \nabla f (z) ||,  \quad  \text{with} \quad z = (1-c)x + cy$$

> Proof:
> The above result is for the multivariate case which is derived from the single variable case as follows.
> 
> Let $f: [a, b] \to \mathbb{R}$ be a continuous function on the closed interval $[a, b]$ and differentiable on the open interval $(a, b)$ then there exists $c \in (a, b)$ such that,
> $$f^{\prime}(c)=\frac{f(b)-f(a)}{b-a}$$
> Now consider the line segment $(1 - t)x + ty$ joining two fixed points $x, y \in G$ with $t \in (0, 1)$. Considering $g(t) = f\big((1 - t)x + ty \big)$ since $g$ is a differentiable function in one variable we have:
> $$  g(1) - g(0) = g'(c) $$
> and so substituting for $g(1) = f(y)$, $g(0)=f(x)$ and for $g'(c)$ using the chain rule gives
> $$ f(y) - f(x) (y - x)^\top f (z), \quad \text{with}  \quad z = (1-c)x + cy$$
> See [Wikipedia](https://en.wikipedia.org/wiki/Mean_value_theorem) for more info


