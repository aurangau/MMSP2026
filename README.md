# Supplementary Material for IEEE MMSP 2026
Supplementary Material for IEEE MMSP 2026
**A Subjective Study on a New Sharpness Informed Class of Metrics**<br />
Authors:<samp>{aurangau, vibhootv, dramsook, anil.kokaram}@tcd.ie</samp>

## Abstract
Perceptual loss functions in Deep Neural Network
(DNN) deblurring architectures improve the overall quality of
restored images. However, few focus on explicitly targeting
sharpness in the restorations. We conduct a subjective study of
models trained with and without losses which explicitly target
sharpness using a four-protocol approach, exploring preferred
sharpness levels and effects on image quality. We introduce a
novel dataset of images with uniform sharpness increments along
with Difference Mean Opinion Scores (DMOS). Additionally,
we propose a novel class of Sharpness Informed (SI) Image
Quality Assessment (IQA) metrics which properly penalize over-
sharpening. Our new SI-PSNR metric outperforms all other
PSNR variants in terms of correlation statistics on IQA bench-
marking datasets. We show that, on average, images restored
using a sharpness-aware composite loss are preferred in 67% of
binarized comparisons, as opposed to losses that do not explicitly
target sharpness.

## Ablation Study on the selection of Hyper-parameters
The equation (5) in our paper is as follows:

$$
L_c = L(I, \tilde{I}) - \beta \cdot Q(\tilde{I})
$$

To produce restoration during training, we may set the hyper-parameter value $\beta$ to either reduce the sharpness of the restorations or increase them. The following experiment was also performed as part of our work [1]  where we examine the effect of $\beta$. This can be seen in Table 1.
| $\beta$ | PSNR (dB) | SSIM | $Q$ | LPIPS
| --- | --- | --- | --- | --- |
| **0** | **35.069** | **0.944** | **0.153** | **0.127**
| 0.001 | 35.102 | 0.945 | 0.152 | 0.117
| 0.01 | 35.101 | 0.945 | 0.154 | 0.117 
| 0.05 | 34.844 | 0.945 | 0.166 | 0.122
| 0.1 | 33.641 | 0.940 | 0.183 | 0.127

A visual example of this phenomenon can be seen below.
| ![Image 1](Beta_Value_Comp/kodim01_blurry.png)| ![Image 2](Beta_Value_Comp/kodim01_b_r_onlyMAE.png) | ![Image 3](Beta_Value_Comp/kodim01_b_r_0_001.png) | 
| --- | --- | --- |
| Blurry Image | $\beta$ = 0 | $\beta$ = 0.001 |

| ![Image 4](Beta_Value_Comp/kodim01_b_r_0_01.png) | ![Image 5](Beta_Value_Comp/kodim01_b_r_0_05.png) | ![Image 6](Beta_Value_Comp/kodim01_b_r_0_1.png) |
| --- | --- | --- |
| $\beta$ = 0.01 | $\beta$ = 0.05 | $\beta$ = 0.1 |

## Sharpness Informed Metrics

## Ablation Study on the Exponentiation of Ringing Detection Ratio
The Ringing Detection Ratio (RDR) or $\alpha$ between a distorted image ($\tilde{I}$) and reference image ($I$) may be defined as follows.

$$
\alpha = \frac{|\tilde{Q} - Q|}{Q}
$$

This ratio measures the increase or decrease in sharpness of the distorted image with respect to the reference image. A higher $\alpha$ intuitively corresponds to more ringing or blur, whereas a lower value corresponds to little ringing or blur. This ratio can be used to construct a ringing map as given in the figure below. In this, the patch size for measuring $\alpha$ has been set to 4. The image size is 512 $\times$ 512. 


![Ringing Detection Map](RDR_Map/rdr_map.png)

To measure the Sharpness Informed (SI) - PSNR, we first measure patch-wise SI-MSE (Equation (2) in the paper) which is as follows.

$$
\text{SI-MSE}(\tilde{I}, I) = \text{MSE}(\tilde{I}, I) \cdot \alpha^\rho
$$

We noticed that exponentiating $\alpha$ to $\rho$ results in better Pearson correlation between the metric (SI-PSNR) and Difference Mean Opinion Scores (DMOS). We perform the exponentiation experiment over two datasets - our proposed dataset and KADID-10K [2].



## Protocol Specifications

## Correlation between Metrics and DMOS

## Dataset on MOS, DMOS and Metric Values

## References
[1] U. Aurangabadkar, D. Ramsook and A. Kokaram, "A Sharpness Based Loss Function for Removing Out-of-Focus Blur," 2024 IEEE 26th International Workshop on Multimedia Signal Processing (MMSP), West Lafayette, IN, USA, 2024, pp. 1-6, doi: 10.1109/MMSP61759.2024.10743912. GitHub Repo - https://github.com/aurangau/MMSP2024

[2] Lin, Hanhe, Vlad Hosu, and Dietmar Saupe. "KADID-10k: A large-scale artificially distorted IQA database." 2019 Eleventh International Conference on Quality of Multimedia Experience (QoMEX). IEEE, 2019.

