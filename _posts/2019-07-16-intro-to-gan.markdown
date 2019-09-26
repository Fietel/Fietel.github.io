---
layout: single
title: "Introduction to Generative Adversarial Networks "
date: 2019-07-16 12:00:00 +0200
categories: GAN
classes: wide
# header:
#   overlay_image: /assets/images/vanillaGAN.png #alternativ: image:
#   excerpt: "Introduction to GANs"
#   image_description: "Basic architecture of a GAN"
# caption: "Photo credit: [**y**](x)"
---

There are a ton of introductions to Generative Adversarial Networks (GANs) out there. I highly recommend to read the [original paper][gan-paper] and some follow up papers. Which one you might find interesting will most likely depend on your application. Generally, rather recent developments like the [Wasserstein GAN (WGAN)][wgan-paper] and some of its' [improvements][improved-wgan] should not only be considered because of their performances, but also because of the additional insights into the whole subject.

Anyways: This post focuses on some of the necessary basics, but also aims to provide the basic knowledge required for the anomaly detection using GANs, which has been investigated in [another blog entry]({%post_url 2019-08-02-anomaly-detection-with-gans%}).
Let's dig into the necessary evil, which might be a repetition of the same chorus you have already heard! I'd be happy for any feedback, I have included the most important sources. I am happy to provide further sources if some facts are less known.

### What are GANs?

GANs are a family of neural networks which do not consist of one, but two neural networks.
One network is called a _discriminator_ $$\mathcal{D}$$ , deciding whether some input comes from a real source of data (i.e. the training set) or from a source that creates _fake_ data.
This source is called the _generator_ $\mathcal{G}$, who aims to generate realistic looking data based on the feedback received from the discriminator. The generator does not have access to the training set and only relies on the feedback of the discriminator, knowing that he has to change _somehow_ if the discriminator correctly identifies its data as synthetic. Contrary to other generative (or probabilistic) models, GANs do not require an a priori parametric specification of a probability distribution function, but they implicitly learn the distribution by a stochastic procedure that defines the data. This procedure usually approximates a corresponding likelihood function during training, which has often been some maximum likelihood estimation. But, while the maxmimum likelihood estimation (which equaly the minimization of the Kullback-Leibler divergence) can be used in combination with GANs, it is not a common way.
The vanilla GAN instead maximizes the Jensen-Shannon divergence, while other distance measures, like the Wasserstein distance, can be used to assert the quality. Some more and comprehensive information can be e.g. found in the [WGAN paper][wgan-paper]

![image](/assets/images/vanillaGAN.png)

To keep this repetition of other introductions short:
GANs apply the minimax algorithm, which is commonly used in game theory to determine the optimal strategy for a finite zero-sum game. In this _game_, we have two players with different utility and cost functions, which should end up in a Nash Equilibrium, where no player has an incentive to change its strategy without a change in strategy of the other player.
In minimax games, all (here: both) player aim to *mini*mize their loss in a *max*imum loss scenrario.
Applied at the problem at hand we receive the following binary cross entropy value function $V(G,D)$

$$
\min_{G} \max_{D}V(D,G)=\mathbb{E}_{x\sim p_{data}(x)}[\text{log } D(\textit{x})]+\mathbb{E}_{z\sim p_{z}(z)}[\text{log }(1-D(G(\textit{z})))]
$$

Here, _x_ is the data from our real distribution, _z_ some noise (usually $z\sim \mathcal{N}(0,1)$ or $z\sim U[-1,1]$) to generate a variety of different data which should encompass some natural diversity and $p_z$ and $p_x$ are the respective distributions.

In summary, $\mathcal{G}$ and $\mathcal{D}$ fight to reduce or increase the log-likelihood of a correct prediction of D. This fight will theoretically end up at a saddle point which is a minimum with respect to the strategy of G and a maximum with respect to the strategy of D.

I will skip the formal definition of the respective goals of each network and their loss functions and other practical hints, since these are commonly found in blog entries, the original paper or [other work you will most likely stumble upon][link-zu-salismus-paper]. Before connecting this with the more important bits required for our anomaly detection, I would like to introduce one of the more common obstacles during training: mode collapse.

### Mode Collapse

Even though GANs have received a lot of attention due to their impressive results in the image domain, especially image generation which has been notoriously difficult, training has been difficult and remains non-trivial.
A big chunk of this difficulty originates from the underlying model: In most models, we use some convex cost function to determine gradients leading us to some (at least local) optimum. These algorithms are not necessarily fit to find a respective Nash Equiilbrium, which leads to non-convergence issues.


[vincent-wgan]: https://vincentherrmann.github.io/blog/wasserstein/
[lilian-wgan]: https://lilianweng.github.io/lil-log/2017/08/20/from-GAN-to-WGAN.html
[gan-paper]: https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf
[wgan-paper]: https://arxiv.org/abs/1701.07875
[improved-wgan]: https://arxiv.org/abs/1704.00028
