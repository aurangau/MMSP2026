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
## Ablation Study on the Exponentiation of Ringing Detection Ratio

## Protocol Specifications

## Correlation between Metrics and DMOS

## Dataset on MOS, DMOS and Metric Values

## References
