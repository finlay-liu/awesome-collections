# CBIR

#### Survey

- SIFT Meets CNN: A Decade Survey of Instance Retrieval
- A Comprehensive Study Over VLAD and Product Quantization in Large-Scale Image Retrieval, **[Code](https://github.com/MKLab-ITI/multimedia-indexing)**
- Recent Advance in Content-based Image
- SIFT Meets CNN A Decade Survey of Instance Retrieval
- Deep Learning for Content-Based Image Retrieval: A Comprehensive Study

#### Dataset

| Dataset Name     | Type           | Content  | Size      | Query Number | Category Number |
| ---------------- | -------------- | -------- | --------- | ------------ | --------------- |
| UKBench          | Retrieval      |          | 10,200    | 2,550        | 2,550           |
| Holidays         | Retrieval      |          | 1,491     | 500          | 500             |
| Oxford-5K        | Retrieval      | Landmark | 6,053     | 55           | 11              |
| Oxford-105K      | Retrieval      | Landmark |           |              |                 |
| Paris-6K         | Retrieval      | Landmark | 6,412     | 500          | 12              |
| Paris-106K       | Retrieval      | Landmark |           |              |                 |
| Flickr1M         |                |          | 1,000,000 | N/A          | N/A             |
| MIR Flickr-1M    |                |          | 1,000,000 | N/A          | N/A             |
| DupImage         |                |          | 1,104     | 108          | 33              |
| FlickrLogos-32   | Retrieval      | Logo     | 8,240     | 500          | 32              |
| INSTRE           |                |          | 28,543    | N/A          | N/A             |
| ZuBuD            |                |          | 1,005     | 115          | 200             |
| SMVS             |                |          | 1,200     | 3,300        | 1,200           |
| MS-COCO          |                |          |           |              |                 |
| ImageNet         | Classification | Landmark |           |              | 1000            |
| Google-Landmarks | Retrieval      | Landmark |           |              |                 |




#### Global Feature Based (Without DL)


#### Local Feature Based

- ASIFT: An Algorithm for Fully Affine Invariant Comparison
- Speeded-Up Robust Features (SURF)    
- Learning Vocabularies over a Fine Quantization
- Object retrieval with large vocabularies and fast spatial matching
- Scalable Recognition with a Vocabulary Tree, **(UKBench Dataset)**
- Visual Categorization with Bags of Keypoints
- ORB: an efficient alternative to SIFT or SURF
- Object Recognition from Local Scale-Invariant Features
- Total Recall: Automatic Query Expansion with a Generative Feature Model for Object Retrieval
- Three things everyone should know to improve object retrieval
- On-the-fly learning for visual search of large-scale image and video datasets
- All about VLAD
- Aggregating localdescriptors into a compact image representatio
- More About VLAD: A Leap from Euclidean to Riemannian Manifolds
- Hamming embedding and weak geometric consistency for large scale image search
- Revisiting the VLAD image representation, **[Code](https://github.com/jorjasso/VLAD/blob/master/VLADlib/VLAD.py)**
- Improving the Fisher Kernel for Large-Scale Image Classification
- Image Classification with the Fisher Vector: Theory and Practice
- Democratic Diffusion Aggregation for ImageRetrieval
- A Vote-and-Verify Strategy for Fast Spatial Verification in Image Retrieval
- Triangulation embedding and democratic aggregation for image search
- Fisher Vector Faces in the Wild
- Compressed Fisher Vectors for Large-Scale Image Classifcation
- Lost in Quantization: Improving Particular Object Retrieval in Large Scale Image Databases
- Large-Scale Image Retrieval with Compressed Fisher Vectors
- BM25 With Exponential IDF for Instance Search
- Lp-norm IDF for Large Scale Image Search
- Object retrieval with large vocabularies and fast spatial matching
- SIFT-Rank: Ordinal Description for Invariant Feature Correspondence

#### Deep Learning Feature (Global Feature)

- Fine-tuning CNN Image Retrieval with No Human Annotation
- Neural Codes for Image RetrievalCompressed    
- Multi-Scale Orderless Pooling of Deep Convolutional Activation Features
- Deep Image Retrieval:Learning Global Representations for Image earch
- End-to-end Learning of Deep Visual Representations for Image retrieval
- What Is the Best Practice for CNNs Applied to Visual Instance Retrieval?
- Bags of Local Convolutional Features for Scalable Instance Search
- Faster R-CNN Features for Instance Search
- Cross-dimensional Weighting for Aggregated Deep Convolutional Features,  **[Code](https://github.com/yahoo/crow)**
- Class-Weighted Convolutional Features for Image Retrieval, **[Code](https://github.com/imatge-upc/retrieval-2017-cam)**
- Multi-Scale Orderless Pooling of Deep Convolutional Activation Features
- Aggregating Deep Convolutional Features for Image Retrieval
- Particular object retrieval with integral max-pooling of CNN activations, **[Code](http://cmp.felk.cvut.cz/~toliageo/soft.html)**
- Particular object retrieval using CNN, **[Code](https://github.com/AaltoVision/Object-Retrieval)**
- Learning to Match Aerial Images with Deep Attentive Architectures
- Siamese Network of Deep Fisher-Vector Descriptors for Image Retrieval]
- Combining Fisher Vector and Convolutional Neural Networks for Image Retrieval
- Selective Deep Convolutional Features for Image Retrieval
- Class-Weighted Convolutional Features for Image Retrieval, **[Code](https://github.com/imatge-upc/retrieval-2017-cam)**
- Towards Good Practices for Image Retrieval Based on CNN Features
- Fine-tuning CNN Image Retrieval with No Human Annotation
- Deep Binaries: Encoding Semantic-Rich Cues for Efficient Textual-Visual Cross Retrieval
- Deep Spatial-Semantic Attention for Fine-Grained Sketch-Based Image Retrieval

#### Deep Learning Feature (Local Feature)

- **affnet**: [Learning Discriminative Affine Regions via Discriminability](http://cn.arxiv.org/pdf/1711.06704.pdf), **[Code](https://github.com/ducha-aiki/affnet)**
- A Large Dataset for Improving Patch Matching, **[Code](https://github.com/rmitra/PS-Dataset)**(PS-Dataset)
- **hardnet**: [Working hard to know your neighbor's margins: Local descriptor learning loss](https://github.com/DagnyT/hardnet)
- **matchnet**: [MatchNet: Unifying Feature and Metric Learning for Patch-Based Matching](https://github.com/hanxf/matchnet)
- DIR
- LIFT
- DELF
- siaMAC
- R-MAC

#### Duplicate(copy) detection
- A New Approach to Image Copy Detection
- A SIFT-Based Forensic Method for Copy-Move Attack Detection and Transformation Recovery
- A Survey of the Image Copy Detection
- A robust detection algorithm for copy-move forgery in digital images
- Detection of Near-duplicate Images for Web Search
- Efficient Near-duplicate Detection and Sub-image Retrieval
- High-Confidence Near-Duplicate Image Detection

#### Useful Package

- [OpenCV](https://opencv.org/)
- [scikit-image](http://scikit-image.org/)
- [dlib](http://dlib.net/)
- [VLFeat](http://www.vlfeat.org/)
- [Yael](http://yael.gforge.inria.fr/)