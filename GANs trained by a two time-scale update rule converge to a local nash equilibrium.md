# GANs Trained by a Two Time-scale Update Rule Converge to a Local Nash Equilibrium  
Martin Heusel, Hubert Ramsauer, Thomas Unterthiner, Bernhard Nessler, Sepp Hochreiter  
LIT AI Lab & Institute of Bioinformatics, Johannes Kepler University Linz

**Origin** NIPS 2017
**Date:** June 2017  
**Labels:** Generative Adversarial Networks (GANs), two time-scale update rule (TTUR), Frechet Inception Distance (FID)

## Summary
The paper proposed a __*two time-scale update rule (TTUR)*__ for training __*GANs*__ with __*Stochastic gradient descent (SGD)*__ on __*arbitrary GAN loss functions*__. Besides, they introduced a new evaluation metric called __*Frechet Inception Distance (FID)*__.
## Application
TTUR improves learning for DCGANs and Improved Wasserstein GANs (WGAN-GP), outperforming conventional GAN training with a one time-scale update rule on CelebA, CIFAR-10, SVHN, LSUN Bedrooms, and the One Billion Word Benchmark.

## Method
1. Evaluation metrics: They use FID and Jensen-Shannon-divergence (JSD)
    
## Novelty
1. Updating rule: TTUR
    * The convergence of GANs has not been proved until then.   
    * TTUR converges under mild assumptions to a stationary local Nash equilibrium using the theory of stochastic approximation.  
    * They proved the convergence can be extended to Adam optimization which follows the dynamics of a heavy ball with friction and thus preferes flat minima in the objective landscape.  
    * TTUR has an individual learning rate for both the discriminator and the generator.  

2. Evaluation metric: FID
    * They claimed FID captures the similarity of generated images to real ones better than Inception Score.   
    * They assume the **_coding units (what is it?)_** to follow a multidimensional Gaussian.     
    * The distance of two Gaussians (synthetic and ground-truth images) is measured by FID.  
    * FID is consistent with increasing disturbance and human judgement (perceptual quality).    
    * FID is more consistent with the noise level than the **_Inception Score (discussed in Notes)_.**   
    
## Notes
This paper mentioned several quality measure metrics, which are summarized below.  

__Likelihood - the best known measure__  
* It can be estimated by annealed importance sampling. 
* Drawbacks:   
    * heavily depends on the noise assumptions for the real data    
    * can be dominated by single samples  
    
__Density estimates__  
* It has drawbacks too (see reference if interested).

__Inception Score - a well-performing approach to measure the performance of GANs__  
* It correlates with human judgement.  
* Generated images are fed into an inception model that was trained on ImageNet.   
    * Images with meaningful objects are supposed to have low label (output) entropy - they belong to few object classes.   
    * The entropy across images should be high - the variance over the images should be large.  
* Drawbacks: the statistics of ground truth are not used and compared to the statistics of generated images.

## My add-ons
