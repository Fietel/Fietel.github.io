---
title: "GAN based anomaly detection - a condensed version of our review"
topic: GAN, paper
collection: posts
permalink: /posts/gan-based-anomaly-detection
---

Anomaly detection based on Generative Adversarial Networks (GANs) is quite similar to other classification approaches:
We have high dimensional data and want to find some separating hyperplane to correctly divide normal and abnormal data.
For high dimensional data this becomes exceedingly difficult (cf. Curse of Dimensionality).

An more special approach is one-class classification. Usually used in a setting with highly imbalanced data, the problems are quite similar as well:
How can we best approximate the separating hyperplane/a convex hull around normal class data such that we can also detect abnormal data as best as possible?

In our review paper '_Anomaly Detection using Generative Adversarial Networks - Reviewing methodological progress and challenges_' (published in SIGKDD Explorations in 2024) we dive a little deeper into this to identify five major obstacles and some ways how they have been tackled:

1. Instable and slow training procedure
2. Improved anomaly detection scores
3. Restrictions to the latent space
4. Contaminated training data
5. Inference speed and accuracy

### Instable and slow training procedure
The instable and slow training procedure is especially problematic for GANs since they are notoriously difficult to train due to several phenomena such as mode collapse. This is less important for other networks such as pure autoencoders or diffusion models.
### Improved anomaly detection scores
One of the most important and famous papers on GAN based anomaly detection is [AnoGAN](https://arxiv.org/abs/1703.05921) which utilizes the reconstruction error (i.e. how similar are real and generated data in the feature space) and the discrimination error (how similar are real and generated data based on the classification of another network). The latter can especially be relevant if the difference in feature space is small and the reconstruction error less stark (which happens frequently). However, the discrimination error can also be prone to problems such as overconfidence. In comparison to AnoGAN which utilizes a linear combination (retrieved via grid search) of both error components, it is important to improve the efficiency and quality of the score combination (e.g. by using SVMs for smaller datasets) as well as the components itself (e.g. by using the difference in latent space as well).
### Restrictions to the latent space
This leads to the restrictions in latent space: many generative models, including GANs, are often used to generalize - beyond the training data and distribution. As soon as this happens anything can happen. Abnormal data can be generated as well. Especially in the one-class setting this could be avoided by leveraging latent information - or other restrictions in the future as well.
### Contaminated training data
Contaminated data is especially important and most often overlooked in academia. Barely any real datasets are completely correctly labeled, sometimes further impacted by shifts in the distribution. To avoid this, it is important to detect or account for falsely annotated data.
### Inference speed and accuracy
The inference speed is once again quite specific to GANs and especially approaches similar to AnoGAN which utilizes a latent optimization scheme to find abnormal data. This does not allow realtime inference. This was e.g. improved by learning an encoding mapping as part of a combination of autoencoders and GANs.

More formal descriptions as well as work going deeper into this can be found in our paper. Please let me know if you have any questions!