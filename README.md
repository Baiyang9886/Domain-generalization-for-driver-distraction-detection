Domain Generalization Method Based on CLIP and Center Loss for Driver Distraction Detection
====

The discrepancy between the actual application scenarios and the training data collection scenarios leads to the domain shift between the training and test data, which restricts the performance of existing driver distraction detection methods in practical applications. To address the domain shift problem and promote the deployment of deep learning models in practical scenarios, in this paper, we propose a domain generalization method based on the contrastive language-image pretraining (CLIP) model and the constraint of center loss (DGCCL) for driver distraction detection. Firstly, the image encoder of the pre-trained CLIP model is adopted as the feature extraction module to improve the domain generalization ability of the proposed model. Furthermore, the constraint of center loss is introduced to promote the samples of different datasets to follow an approximately identical distribution in the feature space, thereby alleviating the domain shift problem. Additionally, the classification loss with additive angular margin penalty (AAMP) is introduced in the proposed model to further improve the cross-domain performance. 

Domain generalization method based on the CLIP model and the constraint of center loss
-------

![Image](https://github.com/Baiyang9886/Domain-generalization-for-driver-distraction-detection/blob/main/%E5%9B%BE%E7%89%871-3.jpg) 
Fig. 1 The schematic diagram of the proposed domain generalization method based on the CLIP model and the constraint of center loss (DGCCL). In this figure, the balls with different color represent the features of different class of samples.

In this study, we propose a domain generalization method based on the CLIP model and the constraint of center loss. The overall schematic diagram of this method is shown in Fig. 1. Firstly, the image encoder of the pretrained CLIP model is adopted for feature extraction from the input images. Then, the constraint of center loss is adopted to deal with the domain shift problem between different datasets. It can promote the convergence of the same class of samples from different datasets to the same region, so that samples from different datasets conform to approximately identical distribution in the feature space. Additionally, to further improve the cross-dataset classification ability of the proposed model, the AAMP is introduced to the softmax-based classification loss of the proposed model. In this study, the training set of multiple different driver distraction detection datasets are mixed as the source domain for model training (as shown in Fig. 1). While the test set of another new dataset is taken as the target domain for model testing. 

![Image](https://github.com/Baiyang9886/Domain-generalization-for-driver-distraction-detection/blob/main/%E5%9B%BE%E7%89%872-1-new.jpg) 
Fig. 2 The schematic diagram of overcoming domain shift problem through the constraint of center loss. In this figure, (a) is the distribution of samples before the training process, and (b) is the sample distribution after sufficient training.

Firstly, the center vectors of each class are initialized randomly. Then, samples from multiple different datasets are mixed for model training. During the training process, the same class of samples from different datasets are promoted to converge to the same region in the feature space by minimizing the center loss (as shown in Fig. 2(a)), which is defined as the average Euclidean distance between the feature vectors and their corresponding center vectors. In order to adapt the center vectors to better reflect the distribution of the corresponding class of samples, the center vectors are updated in the direction of reducing center loss with a certain learning rate $\alpha$ during each training iteration. After sufficient training, the same class of samples will converge within a shared region, and the samples originating from different datasets eventually adhere to approximately identical distribution in the feature space, as shown in Fig. 2(b). Therefore, the proposed domain generalization method based on center loss can effectively address the domain shift problem and significantly improve the cross-domain performance.

### Dataset download link
The dataset SAM-DD consists of two sets of data captured by two cameras simultaneously, one from the front and the other from the right side of the driver. Due to the different shooting angles between these two sets, they can be considered as two distinct domains: SAM-front and SAM-side. Additionally, there are variations in the image size, aspect ratio, and camera positions among the samples in the SAM-DD, AUC-DDD, and State-Farm datasets. Therefore, the samples in the AUC-DDD and State-Farm dataset can be considered as two independent domains. Consequently, data from four distinct domains are involved in the experiments.
<div align="center">

<img src="https://github.com/Baiyang9886/Domain-generalization-for-driver-distraction-detection/blob/main/dataset_samples.jpg" width="1000px">

Fig. 3 Some samples from the four domains. In this figure, samples within the same row originate from the same domain, and samples in the same column share the same category.  

</div>
The data of four distinct domains has been publicly released to all researchers. The download link for the dataset is: https://pan.baidu.com/s/1ehIvBMKQlfgtHQ_S3zcmhg?pwd=61mm   extraction code: 61mm 

### Citation
To be added.
