Domain Generalization Method Based on CLIP and Center Loss for Driver Distraction Detection
====

The discrepancy between the actual application scenarios and the training data collection scenarios leads to the domain shift between the training and test data, which restricts the performance of existing driver distraction detection methods in practical applications. To address the domain shift problem and promote the deployment of deep learning models in practical scenarios, in this paper, we propose a domain generalization method based on the contrastive language-image pretraining (CLIP) model and the constraint of center loss (DGCCL) for driver distraction detection. Firstly, the image encoder of the pre-trained CLIP model is adopted as the feature extraction module to improve the domain generalization ability of the proposed model. Furthermore, the constraint of center loss is introduced to promote the samples of different datasets to follow an approximately identical distribution in the feature space, thereby alleviating the domain shift problem. Additionally, the classification loss with additive angular margin penalty (AAMP) is introduced in the proposed model to further improve the cross-domain performance. In order to demonstrate the effectiveness of the proposed method, extensive experiments have been conducted on three publicly available driver distraction detection datasets: AUC-DDD, State-Farm, and SAM-DD. The experimental results verify that our method can achieve much better performance than various well-known image classification models in the cross-domain driver distraction detection tasks.

Domain generalization method based on the CLIP model and the constraint of center loss
-------

<div align="center">

| Data acquisition system | Representative samples |
| ---------- | -----------|
| ![Image](https://github.com/Baiyang9886/Domain-generalization-for-driver-distraction-detection/blob/main/%E5%9B%BE%E7%89%871-3.jpg) | ![Image](https://github.com/Baiyang9886/Domain-generalization-for-driver-distraction-detection/blob/main/%E5%9B%BE%E7%89%872-1-new.jpg)  |
| Fig. 1 The data acquisition system of the MLI-DER dataset. | Fig. 2 Sample presentation of the MLI-DER dataset. In the figure, the four columns of samples are collected under four different light intensity.  |

</div>

In this paper, we propose a domain generalization method based on the CLIP model and the constraint of center loss. The overall schematic diagram of this method is shown in Fig. 1. Firstly, the image encoder of the pretrained CLIP model is adopted for feature extraction from the input images. Then, the constraint of center loss is adopted to deal with the domain shift problem between different datasets. It can promote the convergence of the same class of samples from different datasets to the same region, so that samples from different datasets conform to approximately identical distribution in the feature space. Additionally, to further improve the cross-dataset classification ability of the proposed model, the AAMP is introduced to the softmax-based classification loss of the proposed model. In this study, the training set of multiple different driver distraction detection datasets are mixed as the source domain for model training (as shown in Fig. 1). While the test set of another new dataset is taken as the target domain for model testing. 

Deep learning algorithms rely on the assumption that the samples in the training and test set conform to i.i.d.. However, there is often distribution shift between the training and test set in the cross-domain tasks, which is named domain shift. Since the i.i.d. assumption cannot be satisfied, conventional models usually perform poorly in the cross-domain tasks. In this paper, a domain generalization method based on center loss is proposed to address the domain shift problem and improve the cross-domain performance of the proposed model. 

Firstly, the center vectors of each class are initialized randomly. Then, samples from multiple different datasets are mixed for model training. During the training process, the same class of samples from different datasets are promoted to converge to the same region in the feature space by minimizing the center loss (as shown in Fig. 2(a)), which is defined as the average Euclidean distance between the feature vectors and their corresponding center vectors. In order to adapt the center vectors to better reflect the distribution of the corresponding class of samples, the center vectors are updated in the direction of reducing center loss with a certain learning rate $\alpha$ during each training iteration. After sufficient training, the same class of samples will converge within a shared region, and the samples originating from different datasets eventually adhere to approximately identical distribution in the feature space, as shown in Fig. 2(b). Therefore, the proposed domain generalization method based on center loss can effectively address the domain shift problem and significantly improve the cross-domain performance.
