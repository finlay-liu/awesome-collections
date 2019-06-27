# Deep Learning in Computer Vision

### Image Classification

The task in Image Classification is to predict a single label (or a distribution over labels as shown here to indicate our confidence) for a given image. Images are 3-dimensional arrays of integers from 0 to 255, of size Width x Height x 3. The 3 represents the three color channels Red, Green, Blue. 

- Muti-Class Image Classification

- One/Zero-Shot Image Classification

- Fiine-grained image Classification

- Model quantization 

#### Dataset

| Dataset Name    | Content | Size | Nunber of  categories |
| --------------- | ------- | ---- | --------------------- |
| MNIST           |         |      | 10                    |
| Fashion-MNIST   |         |      | 10                    |
| CIFAR-10/100    |         |      | 10/100                |
| Caltech-101/256 |         |      | 101/256               |
| STL-10          |         |      |                       |
| ImageNet        |         |      | 1000                  |

#### Model

There are the model evaluation in ImageNet dataset.

<https://github.com/Cadene/pretrained-models.pytorch> 

| Model               | Size | Acc@1  | Acc@5  |
| ------------------- | ---- | ------ | ------ |
| EfficientNet-B5     |      | 83.2   |        |
| PNASNet-5-Large     |      | 82.858 | 96.182 |
| EfficientNet-B4     |      | 83.6   |        |
| NASNet-A-Large      |      | 82.693 | 96.163 |
| EfficientNet-B3     |      | 81.0   |        |
| SENet154            |      | 81.32  | 95.53  |
| PolyNet             |      | 81.002 | 95.624 |
| InceptionResNetV2   |      | 80.4   | 95.3   |
| InceptionV4         |      | 80.2   | 95.3   |
| SE-ResNeXt101_32x4d |      | 80.19  | 95.04  |
| InceptionResNetV2   |      | 80.170 | 95.234 |
| InceptionV4         |      | 80.062 | 94.926 |
| EfficientNet-B2     |      | 79.8   |        |
| Xception            |      | 79.000 | 94.500 |
| EfficientNet-B1     |      | 78.8   |        |
| SE-ResNet152        |      | 78.66  | 94.46  |
| ResNet152           |      | 78.428 | 94.110 |
| SE-ResNet101        |      | 78.25  | 94.28  |
| SE-ResNet50         |      | 77.63  | 93.64  |
| DenseNet161         |      | 77.560 | 93.798 |
| ResNet101           |      | 77.438 | 93.672 |
| InceptionV3         |      | 77.294 | 93.454 |
| EfficientNet-B0     |      | 76.8   |        |
| ResNet50            |      | 76.002 | 92.980 |
| VGG19_BN            |      | 74.266 | 92.066 |
| ResNet34            |      | 73.554 | 91.456 |
| VGG16_BN            |      | 73.518 | 91.608 |
| VGG19               |      | 72.080 | 90.822 |
| VGG16               |      | 71.636 | 90.354 |
| ResNet18            |      | 70.142 | 89.274 |
| VGG13               |      | 69.662 | 89.264 |
| VGG11               |      | 68.970 | 88.746 |
| SqueezeNet1_0       |      | 58.108 | 80.428 |
| Alexnet             |      | 56.432 | 79.194 |

#### Link

- https://arxiv.org/abs/1812.01187

### Object Detection

**Object detection** is a computer technology related to computer vision and image processing that deals with**detecting** instances of semantic **objects** of a certain class (such as humans, buildings, or cars) in digital images and videos. 

#### Dataset

| Dataset Name       | Content | Size | Nunber of  categories |
| ------------------ | ------- | ---- | --------------------- |
| PASCAL VOC         |         |      | 80                    |
| MS COCO            |         |      | 200                   |
| Google Open Images |         |      | 500                   |

#### Model

TODO

#### Link

- https://arxiv.org/pdf/1905.05055.pdf
- https://arxiv.org/abs/1906.07155
- https://arxiv.org/abs/1902.04103
- https://arxiv.org/abs/1903.05831

### Image Segmentation

#### Dataset

| Dataset Name      | Content | Size | Nunber of  categories |
| ----------------- | ------- | ---- | --------------------- |
| PASCAL VOC        |         |      |                       |
| MS COCO           |         |      |                       |
| Cityscapes        |         |      | 30                    |
| CamVid            |         |      | 32                    |
| ADE20K            |         |      |                       |
| NYU Depth Dataset |         |      |                       |
| SUN RGB-D         |         |      |                       |

### Video

#### Dataset

| Dataset Name                | Type           | Size      | Nunber of  categories |
| --------------------------- | -------------- | --------- | --------------------- |
| UCF-101                     | Classification | 13,320    | 101                   |
| HMDB51                      | Classification |           |                       |
| Sports-1M                   | Classification | 1,133,157 | 487                   |
| YouTube 8M                  | Classification | 6.1M      | 3862                  |
| Atomic Visual Actions (AVA) |                |           |                       |
| Moments in Time (MIT)       |                |           |                       |
| LSMDC                       |                |           |                       |

#### Model

http://cs231n.stanford.edu/slides/2018/cs231n_2018_ds08.pdf 

http://vision.stanford.edu/pdf/karpathy14.pdf
